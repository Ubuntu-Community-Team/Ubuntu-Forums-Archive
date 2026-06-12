---
title: "Urgent! Ubuntu wont boot!"
date: 2010-09-27
forum: General Help
---

### Post by Jonny87 on 2010-09-27
My dad has done something to his comp and it won't boot.  it stops on boot up an comes up with some sort of black screen command line. he said its something along the lines of "initramfs" and he can't seem to do anything. We tried booting to the recovery console from the grub menu and gets the same response.

Hes having trouble booting to cd at the moment so I need to know is there some sort of command that will fix or at least give some help that he can type in from this spot.

---

### Post by andrewthomas on 2010-09-27
Check this out.

[https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)

---

### Post by searchfgold6789 on 2010-09-27
Could you try to reproduce the exact error? If it is very long, could you give us more details?

---

### Post by Jonny87 on 2010-09-27
> **searchfgold6789 said:**
> Could you try to reproduce the exact error? If it is very long, could you give us more details?

Stay tuned on that, I'll wait for my dad to ring me back so that I can get him to tell me word for word.

---

### Post by JayD239 on 2010-09-27
> My dad has done something to his comp and it won't boot.

Any chance of a more detailed description about what dad did? Was it a hardware or software thing? Any message on the screen worth taking a picture of?

The symptoms (except the initramfs mention) remind me of a problem I had with having too many usb-hubs connected. Try booting without any usb device connected (well maybe mouse and keyboard, but remove all hubs)

---

### Post by Jonny87 on 2010-09-27
> busybox v1.13.3 (ubuntu1:1.13.3.1 ubuntu11) built-in shell (ash) not found try passing target filesystem dos ethre sbin init=boot rag
This is apparently the error code that came up. 

Hes got it booting to a Kubuntu cd now but it seem that there may be an error with the cd that he burnt as it won't fully boot to the live desktop. He can't seem to get his official Ubuntu disk to boot though, this is the official disk that he ordered and had sent to him.

Does the above error mean anything to anyone?

---

### Post by searchfgold6789 on 2010-09-27
This could mean anything, unfortunately...
Does your dad remember what he did to make this happen? We will probably be able to come up with something to undo whatever he did to get the busybox error.

---

### Post by Jonny87 on 2010-09-27
> **searchfgold6789 said:**
> This could mean anything, unfortunately...
Does your dad remember what he did to make this happen? We will probably be able to come up with something to undo whatever he did to get the busybox error.

Well yesterday I got him to do a couple thing such as make kdm the default as it was what he was wanting get rid the gnome start up. we also tryied installing some printer drivers. he said after that it took along time to boot the next time he booted, once it was booted he used it normally doing nothing out of the ordinary. It was the next time he booted after that, that it came up with the error.

---

### Post by Jonny87 on 2010-09-27
Hes still having trouble booting to a liveCD, he cant seem to get it to boot any further than the first menu to choose whether to "try with out installing" "install" etc.
This suggests to me either a bad cd image or hardware problem.
Please, if any one can suggest another way to fix this, I'd love to hear it. He needs his computer and as I'm the one that got him on to Ubuntu I feel partly responsible, even more so as it was me that said hey try install kde and see what you think of that and try this...

---

### Post by searchfgold6789 on 2010-09-27
To clarify:

[LIST]
[*]You're getting an initramfs error after trying to make it so that you booted directly to the kde desktop instead of the kubuntu desktop.
[*]You now have printer drivers
[*]You can't boot into a Live Kubuntu CD past the main menu
[/LIST]
It would help to know the exact process that you went through to try to set the default desktop environment, but it seems like you might not remember that too well...
You may have to make another Live CD and try that. You might wind up having to recover some data with the Live CD and reinstall. Remember to not use sharpie marker on the CD; burn at lowest possible speed; checksum; etc.

I wish you good luck :?

---

### Post by Jonny87 on 2010-09-27
> **searchfgold6789 said:**
> To clarify:

[LIST]
[*]You're getting an initramfs error after trying to make it so that you booted directly to the kde desktop instead of the kubuntu desktop.
[*]You now have printer drivers
[*]You can't boot into a Live Kubuntu CD past the main menu
[/LIST]
It would help to know the exact process that you went through to try to set the default desktop environment, but it seems like you might not remember that too well...
You may have to make another Live CD and try that. You might wind up having to recover some data with the Live CD and reinstall. Remember to not use sharpie marker on the CD; burn at lowest possible speed; checksum; etc.

I wish you good luck :?
Thanks for your help so far.

To get KDE he installed KDE-full then I suggested for him to install Kubuntu-desktop from synaptic to get some some of the additional packages that go with it. To set kdm as default I told him to find the kdm package in synaptic, select it and then select configure from the packages menu. this brought up the option to set kdm or gdm as default.
As for the printer drivers I talked him through install some drivers that he downloaded from the Canon site, either he did something different from what I told him or he got the wrong driver as he lost full ability to print where as before he could print but the pict was all bung.
As far as booting to LiveCD, I think its both the Kubuntu and Ubuntu CD that he's having trouble with. I don't think he can burn another CD as this is his only comp available to him at the moment.

---

### Post by Jonny87 on 2010-09-27
*Bumb*
Does anyone have any ideas?

---

