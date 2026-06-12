---
title: "NetworkManager not working for wireless"
date: 2006-06-23
forum: General Help
---

### Post by JackDog on 2006-06-23
I have an miniPCI orinico card that works great with the default network settings in gnome. When I try to use NetworkManager I it never connects and I see the following in the logs:

```
Jun 22 23:05:05 localhost dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
Jun 22 23:05:05 localhost dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = -1
```

The AP is using 128b WEP with a Hex key. My other laptop (running ubuntu) works fine, this one gets this error. Any ideas? I have googled but have not found an answer. I need network manager to work so that my family can use this laptop easier.

---

