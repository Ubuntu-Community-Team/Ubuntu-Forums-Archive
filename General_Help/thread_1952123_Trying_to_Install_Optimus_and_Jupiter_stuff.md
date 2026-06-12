---
title: "Trying to Install Optimus and Jupiter stuff"
date: 2012-04-03
forum: General Help
---

### Post by LFX64 on 2012-04-03
Neither will work because of the following - displayed in terminal: 

sudo add-apt-repository ppa:wedupd8team/jupiterTraceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 88, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 83, in get_ppa_info_from_lp
    return json.loads(lp_page)
  File "/usr/lib/python2.7/json/__init__.py", line 326, in loads
    return _default_decoder.decode(s)
  File "/usr/lib/python2.7/json/decoder.py", line 366, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
  File "/usr/lib/python2.7/json/decoder.py", line 384, in raw_decode
    raise ValueError("No JSON object could be decoded")
ValueError: No JSON object could be decoded

I'd like to get these working. I'm on 11.10 at the moment and I've not long had it, an I doubt 12.04 is going to be THAT much better with power management.

According to sudo grep rate /proc/acpi/battery/BAT0/state it's using over 2600mA roughly with the screen dimmed when inactive for a few moments, 2900-3000mA on maximum brightness and 2730-2800 roughly when I halve the brightness bar. When plugged into the mains it uses 4331mA.

I am using a Dell XPS L702X with Ubuntu 11.10 64-bit on a Core i5-2540m Sandybridge processor @ 2.6Ghz. I halved my HDD and shared the space. Half with Windows 7, half with Ubuntu. I did it for when 12.04 comes out but I hadn't the patience and I'm not too keen on Windows and their thievery. 

I really do hope that 12.04 has a lot more to offer than whatever is in those notes. Forgetting brightness settings in 11.10 seems a bit daft.

Appreciate the help for those who can offer it. ):P

---

### Post by LFX64 on 2012-04-03
OK Jupiter isn't so cool. I'll leave it on my system anyway, but I'll try Optimus instead, since I have a GT550m sitting inside my laptop with Intel HD 3000 graphics on the CPU. Will Jupiter conflict with Optimus? I really wished Nvidia would release open sourced drivers for their cards.

:D

---

