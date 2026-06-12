---
title: "Help with fdisk -l"
date: 2011-02-19
forum: General Help
---

### Post by |{urse on 2011-02-19
Hi, I paste a little string of basic shell commands to help gather system info while I'm ssh'd into my various systems. I know there are other tools that do this very same thing but I'd rather just keep this in M8 and paste it when i need to.

> touch log && echo $USER && uname -r && date && dmesg | tail && cat /proc/cpuinfo && ifconfig eth0 | sed -rn 's/^.*inet addr:([^ ]+).*$/\1/p' && lspci && sudo fdisk -l  > log  && cat log


I'm curious, is there any way to issue the fdisk -l command while not root? If I can't, oh well, but was just curious if anyone knew a way. 

Even a utility that gathers partition info and outputs similar to fdisk's format would be okay also, so long as i dont have to install it on every machine.

---

### Post by cjhabs on 2011-02-20
You can do this with "palimpsest" - however it is graphical, which doesn't look like what you are trying to do in your script. But, if you ssh with the -X option is works fine over a remote connection.

---

### Post by |{urse on 2011-02-20
yeah, I was kind of hoping to keep it cli. Thx for the effort though =)

---

