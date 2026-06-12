---
title: "Problem with deleted partitions - computer doesn`t work any more."
date: 2012-07-03
forum: General Help
---

### Post by enton on 2012-07-03
Hello,

I had "Windows Starter 7" and Ubuntu on my netbook. I wanted to deinstall Ubuntu and therefore I deleted two partitions - unfortunately, something went wrong. Everytime I start my computer, I get the lines:
"_[COLOR=Black]error: no such partition. grub rescue>[/COLOR]_"

So I wanted to "[COLOR=Red]boot[/COLOR]" my system. I`ve downloaded different boot programms (don`t know the right word for it) and saved them on a [COLOR=Red]CD[/COLOR] or on an [COLOR=Red]USB-stick.
 [/COLOR]
When I restart my computer, I always open "Phoenix SecureCore" and I change the priority, so that my USB-stick and my CDs are read first. 
When I press the button F10, the changes are saved and the computer restarts again. 
After all that: NOTHING happens! I always get those stupid lines: "error: no such partition ....". :(
My CD drive and USB-stick are new and work fine. 

**My question:** What can I do, so that my netbook starts to read the files on my USB-stick or my CDs? 

I tried it with the Live-CD from [COLOR=Green]Ubuntu 12.04 [/COLOR]and the [COLOR=Green]Windows Recovery [/COLOR]CD. I also tried "[COLOR=Green]Unetbootin[/COLOR]" to start both on an USB-stick. I don`t have a Windows Installer CD, because my Windows came with the netbook - I can borrow it, but I am not sure, if the computer will read the CD. 

My netbook is a "Samsung N220 Plus".
Setup Utility: Phoenix SecureCore (tm)


Please help me! (T_T)

---

### Post by efflandt on 2012-07-03
On some computers even if you change drive boot order you may still need to press a specific key during BIOS splash to boot from removable media.  The BIOS splash screen should say what key that is (typically F12 or Esc).  Although, on a netbook size tablet PC I had to enable BIOS to even list the F12 key during splash.

You need to restore a DOS/Windows like mbr.  If you can boot Ubuntu on CD or USB you can use the mbr.bin from syslinux:
[FONT=monospace]
[/FONT]dd bs=440 count=1 conv=notrunc if=/usr/lib/syslinux/mbr.bin of=/dev/sda

---

### Post by enton on 2012-07-03
wow, really fast answer. thank you very much. 

so i need MBR. i read on the internet, that the most easiest way to restore MBR is to use a windows-install-cd. unfortunately i have to ask a friend for it. i hope i can fix it on this weekend. but i am glad that there is hope again.^^ 

is there a possibility to install mbr without a windows-cd? 
if it is too complicated - i prefer to wait until i got the windows-cd. because i don`t want to do more damages to my computer than i already have.

---

