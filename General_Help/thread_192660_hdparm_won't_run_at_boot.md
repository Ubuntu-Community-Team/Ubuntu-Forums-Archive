---
title: "hdparm won't run at boot"
date: 2006-06-09
forum: General Help
---

### Post by jazzgossen on 2006-06-09
I set up my /etc/hdparm.conf with the following settings:

command_line {
	hdparm -S 12 /dev/hda
	hdparm -y /dev/hda
}

I would then expect /dev/hda to spin down immediately after startup, or at least within one minute (12x5 seconds), but it doesn't. 

Is there anything else I need to do? If I run the commands manually after boot, it works, but I want this particular disk to spin only while making scheduled backups.

---

### Post by ticool on 2006-06-09
Instead of writing these things into the hdparm.conf you just add the -k1 flag in the commandline...

example: hdparm -d1 -c1 -k1 /dev/hdX   

This will also save your parameters even after reboot!

---

### Post by scxtt on 2006-06-09
i think hdparm.conf is VERY picky on config ...

i wasn't even able to use:

/dev/hdb
{
(a tab)dma = on
}

the 1st { HAD to be on the same line as /dev/hdb ...

so, i suggest something like:

command_line_1 {
(a tab)hdparm -S 12 /dev/hda
}

command_line_2 {
(a tab)hdparm -y /dev/hda
}

---

### Post by stanz on 2006-06-25
[quote=scxtt]i think hdparm.conf is VERY picky on config ...the 1st { HAD to be on the same line as /dev/hdb ...so, i suggest something like:
#
command_line_1 {
(a tab)hdparm -S 12 /dev/hda
}
#
command_line_2 {
(a tab)hdparm -y /dev/hda
}
#[/quote] Your suggestion is right, as shown in the 'conf' file- examples.
Has anyone made their own script~ for rcS.d ?
any joy?   errors at boot? :rolleyes:

---

