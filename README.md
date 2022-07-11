aws-ip-ranges-parser
====================

The ansible role parses https://ip-ranges.amazonaws.com/ip-ranges.json and create variables split by categories.
It was designed to prepare and use AWS prefixes in other ansible roles.
[AWS IP address ranges](https://docs.aws.amazon.com/general/latest/gr/aws-ip-ranges.html)

Requirements
------------

The role is tested with the following specific software versions:
* Ansible: 2.11.12
* Ansible: 2.13.1
* Ubuntu: 18
* Ubuntu: 20

Role Input Variables
--------------------

The role defines most of its variables in `defaults/main.yml`:

### `aws_ip_ranges_parser_ipv4_enabled`
- Process IPv4 prefixes?
- Default value: **true**

### `aws_ip_ranges_parser_ipv6_enabled`
- Process IPv6 prefixes?
- Default value: **false**

### `aws_ip_ranges_parser_print_results`
- Print results?
- Default value: **true**

### `aws_ip_ranges_parser_regions`
- Comma-separated region list
- Default value: **all**

### `aws_ip_ranges_parser_services`
- Comma-separated service list
- Default value: **''**

### `aws_ip_ranges_parser_network_border_groups`
- Comma-separated network border group list
- Default value: **''**

Role Output Variables
---------------------

Output variables could be used in other roles

### `aws_ipv4_prefixes_all`
- All AWS IPv4 prefixes
- Example: ["1.1.1.1/32", "2.2.2.0/24", ...]

### `aws_ipv4_regions_all`
- All AWS IPv4 regions
- Example: ["us-east-1", "eu-central-1", ...]

### `aws_ipv4_services_all`
- All AWS IPv4 services
- Example: ["EC2", "API_GATEWAY", ...]

### `aws_ipv4_network_border_groups_all`
- All AWS IPv4 network border groups
- Example: {"us-east-1": ["1.1.1.1/32", "2.2.2.0/24", ...], ...}

### `aws_ipv4_prefixes_by_region`
- IPv4 prefixes split by region
- Example: {"us-east-1": ["1.1.1.1/32", "2.2.2.0/24", ...], ...}

### `aws_ipv4_prefixes_by_service`
- IPv4 prefixes split by service
- Example: {"EC2": ["1.1.1.1/32", "2.2.2.0/24", ...], ...}

### `aws_ipv4_prefixes_by_network_border_group`
- IPv4 prefixes split by network border group
- Example: {"us-east-1": ["1.1.1.1/32", "2.2.2.0/24", ...], ...}

### `aws_ipv6_prefixes_all`
- All AWS IPv6 prefixes
- Example: ["2a05:d018::/36", "2406:dafc:f000::/40", ...]

### `aws_ipv6_regions_all`
- All AWS IPv6 regions
- Example: ["us-east-1", "eu-central-1", ...]

### `aws_ipv6_services_all`
- All AWS IPv6 services
- Example: ["EC2", "API_GATEWAY", ...]

### `aws_ipv6_network_border_groups_all`
- All AWS IPv6 network border groups
- Example: {"us-east-1": ["2a05:d018::/36", "2406:dafc:f000::/40", ...], ...}

### `aws_ipv6_prefixes_by_region`
- IPv6 prefixes split by region
- Example: {"us-east-1": ["2a05:d018::/36", "2406:dafc:f000::/40", ...], ...}

### `aws_ipv6_prefixes_by_service`
- IPv6 prefixes split by service
- Example: {"EC2": ["2a05:d018::/36", "2406:dafc:f000::/40", ...], ...}

### `aws_ipv6_prefixes_by_network_border_group`
- IPv6 prefixes split by network border group
- Example: {"us-east-1": ["2a05:d018::/36", "2406:dafc:f000::/40", ...], ...}

Dependencies
------------

- ansible collections are specified in `requirements.yml`
- pip packages are specified in `requirements-pip.txt`

```bash
ansible-galaxy collection install -r requirements.yml
pip install -r requirements-pip.txt
```

Example Playbook
----------------

Basic parsing is possible using the included `pb-default.yml` playbook:

```
ansible-playbook pb-default.yml
```

You can also simply pass variables in using the `--extra-vars/-e` option to the
`ansible-playbook` command:

```
ansible-playbook pb-default.yml --extra-vars "aws_ip_ranges_parser_regions='us-east-1,eu-central-1'"
```

License
-------

BSD

Author Information
------------------

[Alexandr Pomeshkin](https://www.linkedin.com/in/alexandr-pomeshkin-400519146/)
