---
title: "Dual boot with 2 HDDs"
date: 2009-09-02
forum: General Help
---

### Post by ibrabeicker on 2009-09-02
hello there

i had a single HDD that stored my win xp and my ubuntu, to choose wich OS i want i use GRUB.

Now i have a second HDD with windows 7 on it and i would like to know a way to put the windows 7 option in grub. Currently i need to change the primary and secondary HDD boot manually with the BIIOS setup 


thanks

---

### Post by philinux on 2009-09-02
Have a look through these. You need to use the grub command chainloader.

[http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=q5X&q=grub+windows+xp+chainloader&revid=963816013&ei=speeSuDMHcr2-Ab6qKnaCw&sa=X&oi=revisions_inline&resnum=0&ct=broad-revision&cd=1](http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=q5X&q=grub+windows+xp+chainloader&revid=963816013&ei=speeSuDMHcr2-Ab6qKnaCw&sa=X&oi=revisions_inline&resnum=0&ct=broad-revision&cd=1)

---

### Post by ibrabeicker on 2009-09-04
ok I will end my own thread because i found a simple solution


go to /boot/grub/menu.lst and edit it as root

add the following text to the file

title Windows NT / Windows 95 boot menu
root        (hd1,0)
makeactive
chainloader +1


the part where you add (hd1,0) means grub will search for a boot from the hd 1(the second in your computer, the first is hd0), and the second zero is for the first partition in your second hd.

---

