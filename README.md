# Cisco Packet Tracer VLAN Segmentation Lab

Cisco Packet Tracer VLAN lab illustrating department-based Layer 2 segmentation across two switches.

## Project Overview

This project documents a department-based VLAN topology across two switches. The screenshot groups endpoint PCs into IT, CSE, and ADS department areas and labels the VLANs as VLAN 10, VLAN 20, and VLAN 30. A dashed inter-switch link is visible, consistent with a link intended to carry multiple VLANs.

## Features

- Two-switch topology with multiple endpoint PCs
- Department grouping for IT, CSE, and ADS
- VLAN 10, VLAN 20, and VLAN 30 labels
- Inter-switch link shown between the switches
- Verification command examples for VLAN and trunk status

## Technologies Used

- Cisco Packet Tracer
- Cisco Catalyst 2960 switch model (as shown)
- VLANs
- 802.1Q trunking concepts
- Ethernet

## Project Structure

```text
packet-tracer-vlan-segmentation-lab/
├── README.md
└── screenshots/
    └── [project screenshots]
```

## Network Topology Details

The screenshot shows two access switches connected by a dashed inter-switch link. IT endpoints are labeled VLAN 10, CSE endpoints VLAN 20, and ADS endpoints VLAN 30. The screenshot includes network labels `192.168.10.0` and `192.168.20.0`; it does not clearly show a separate subnet for VLAN 30 or the exact switchport assignments. Treat IP addressing and port mappings as a design example to complete during recreation.

## How to Recreate and Test

1. Add two 2960 switches and the required PCs.
2. Connect each PC to its local switch with copper straight-through cables.
3. Connect the switches together; configure the inter-switch interfaces as an 802.1Q trunk if supported by the selected Packet Tracer devices.
4. Create VLANs 10, 20, and 30 on both switches and name them according to the departments.
5. Assign each PC-facing switchport to the appropriate access VLAN.
6. Plan a unique IP subnet per VLAN. For example, use `192.168.10.0/24`, `192.168.20.0/24`, and a third distinct subnet for VLAN 30. Configure each PC with an address in its VLAN's subnet.
7. Test same-VLAN connectivity across the trunk. Inter-VLAN communication requires a Layer 3 device and appropriate routing; a Layer 2 switch alone will not route between VLANs.

## Useful Verification Commands

```text
enable
show vlan brief
show interfaces trunk
show interfaces status
show running-config

# Example access-port configuration (replace interface and VLAN as needed)
configure terminal
vlan 10
 name IT
vlan 20
 name CSE
vlan 30
 name ADS
interface fastethernet0/1
 switchport mode access
 switchport access vlan 10
end
show vlan brief
```

## Expected Results

- `show vlan brief` lists VLANs 10, 20, and 30 with the intended access ports.
- `show interfaces trunk` shows the inter-switch link as trunking after it is configured correctly.
- Hosts in the same VLAN and subnet should be able to communicate across the trunk.
- Hosts in different VLANs should not communicate directly without inter-VLAN routing.

## Screenshots

![Vlan Segmentation Topology](screenshots/vlan-segmentation-topology.jpg)

## Important Notes

- The original `.pkt` file was not provided. This repository contains documentation and the supplied screenshot only.
- The screenshot does not expose every port assignment or a complete IP addressing plan; those details must be chosen and configured during recreation.
- Commands are examples, not a tested configuration. Adjust interface identifiers to match your topology.

## Portfolio Use

This project is suitable as a networking lab documentation sample for a student portfolio. Before presenting it as a completed practical implementation, recreate the topology in Cisco Packet Tracer, verify the configuration, and add the resulting `.pkt` file and your own test evidence.
