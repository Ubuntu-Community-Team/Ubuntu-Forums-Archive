---
title: "bash completion"
date: 2006-04-15
forum: General Help
---

### Post by VoiDgr on 2006-04-15
I used to have mandriva. Migration was very easy (i just slightly miss the control center thing with its drakes) and i really like adept/synaptic (if only it had a gui for apt-file search it would be perfect).

My problem is that I just can't get used to the way bash completion works in kubuntu. In kubuntu, when you press [tab] there is only a beep. You have to press it a second time to get the suggestions. In mandriva, the first time you press [tab] it shows the suggestions and there is no beep. 

I did some googling but it was no good. Do you know what i have to edit to get this behaviour?

---

### Post by ComplexNumber on 2006-04-15
> In kubuntu, when you press [tab] there is only a beep. You have to press it a second time to get the suggestions. In mandriva, the first time you press [tab] it shows the suggestions and there is no beep.
don't worry, it works that way on suse and fedora too (although, i'll have to check later to be 100%, but i'm pretty certain they are). it would seem that mandriva is the odd one out. come to think of it, i remember it being 1 press in mandrake/mandriva.

---

### Post by VoiDgr on 2006-04-16
[QUOTE=ComplexNumber]don't worry, it works that way on suse and fedora too (although, i'll have to check later to be 100%, but i'm pretty certain they are). it would seem that mandriva is the odd one out. come to think of it, i remember it being 1 press in mandrake/mandriva.[/QUOTE]

You' re right, at least about suse. But, it seems to me, that the mandriva way is more user-friendly. At least more VoiDgr-friendly :-)

I guess someone has to edit something in /etc/bash.bashrc and/or /etc/bash_completion. But I'm not in the mood to read the whole bash documentation to find it :-)

---

### Post by fdoving on 2006-04-16
Try to install the 'kio-apt' package and use apt:/ in konqueror for your apt searching needs.

- Frode

---

### Post by VoiDgr on 2006-04-16
[QUOTE=fdoving]Try to install the 'kio-apt' package and use apt:/ in konqueror for your apt searching needs.

- Frode[/QUOTE]


Thanks! Nice tip.

---

### Post by VoiDgr on 2006-04-18
> My problem is that I just can't get used to the way bash completion works in kubuntu. In kubuntu, when you press [tab] there is only a beep. You have to press it a second time to get the suggestions. In mandriva, the first time you press [tab] it shows the suggestions and there is no beep.

Well, i found it. If anyone else is intrested, he/she has to add:
```
set show-all-if-ambiguous on
```
in /etc/inputrc

---

