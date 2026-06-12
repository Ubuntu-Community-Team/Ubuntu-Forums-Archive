---
title: "J2EE installation problems"
date: 2006-02-20
forum: General Help
---

### Post by WujekSamoZlo on 2006-02-20
I dowlnoaded it from the Sun website - the whole bundle. It's a .bin file. I used the chmod +x xommand, but it doesn't work.
When I type:
j2eesdk-1_4_03-linux.bin
it says:
bash: j2eesdk-1_4_03-linux.bin: command not found
So I tried:
sh j2eesdk-1_4_03-linux.bin
and the response was:
j2eesdk-1_4_03-linux.bin: j2eesdk-1_4_03-linux.bin: cannot execute binary file

What am I supposed to do? Did anybody faced similar problems or is it just me?

---

### Post by gingermark on 2006-02-21
I had a quick look at the Sun Installation guide.

try

**./**j2eesdk-1_4_03-linux.bin

I assume you actually NEED the enterprise edition? I only ask as the Standard Editions are available in the repositories (add the [PLF repository](http://doc.ubuntu-fr.org/doc/plf) to your /etc/apt/sources.list file to get them...)

---

