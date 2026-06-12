---
title: "New to Ubuntu.."
date: 2011-01-10
forum: General Help
---

### Post by Cjaster on 2011-01-10
Hello :D
I have an odd problem..
I installed Ubuntu(Gnome) through WUBI
I installed it and after 2 days I decided to update it.. 
First it asked me to install nVidia drivers. I did so I didn't have to boot using low graphics
Then I installed all the latest updates..
I shut it down and moved on..
(I am currently Dual booting Vista and Ubuntu)
I tried to load into Ubuntu and there was 2 different version I could boot into(And the safe mode of these versions) 2.4.(?) and 2.4.7(generic)
When I tried to boot into 2.4.7 it hung on the blinking line...(_)
I tried the older version and it booted fine..
The drivers work fine.. When it came up it said there were some kind of errors..(Gnome related i believe)
I closed its all fine now... 
Should I be worried about anything(Sorry about the lack of info. Never did this before) :confused:

---

### Post by blakep2 on 2011-01-11
so what seems to be the problem, I am not understanding

---

### Post by mastablasta on 2011-01-11
Dont upgrade Wubi. you can update it but take precautions not to update GRUB.
 
Having different kernels is normal in linux. they are there in case new one doens't work well, so you can drop back to the older one.
 
i hope you use wubi only as trial version and not produciton. because wubi uses virtualisation. it's not propper OS install. it has some issues. for example everything you do is made in very large fire. if that file get's corrupted you might end up loosing everything you did under wubi,

---

### Post by veggen on 2011-01-11
If it was an one-time error I wouldn't worry to much.
If you're puzzled by having different versions, you can easily remove the older kernel from synaptic, if the newer works fine.

---

