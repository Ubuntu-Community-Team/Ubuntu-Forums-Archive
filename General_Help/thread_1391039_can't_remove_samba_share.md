---
title: "can't remove samba share"
date: 2010-01-26
forum: General Help
---

### Post by llawwehttam on 2010-01-26
I just set up a quick share to allow another computer to get some files. I then noticed I was already sharing another folder elsewhere that I had forgotten to stop sharing so I stopped it from sharing.

 When I got the files I wanted on my other computer I went to stop the share I had just set up but it appeared to be unshared even though I can see and access it on the network.

Any ideas how to stop this share?

EDIT: [https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/250464](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/250464) a bit like this bug but with a folder not a CD.

I have tried renaming the folder. When I do this the share disappears from the network but when I name it back again the share re-activates. There is no icon telling me the folder is shared.

I have tried rebooting, restarting the samba service and restarting nautilus but its still invisibly shared.

---

### Post by llawwehttam on 2010-01-26
Just wondering if there is a way to manually tell samba not to share a folder as the bug seems to be with nautilus.

---

### Post by t4thfavor on 2010-01-26
Look for the entry in the file /etc/samba/smb.conf

There will be a bunch of stuff in that file, your share should be one part of it.


Back it up first in case you break something.

---

### Post by danastasio on 2010-01-26
did you try removing the share from your smb.conf file?

---

### Post by llawwehttam on 2010-01-26
I have managed to do it through nautilus in the end. I was about to resort to semving the entry in smb.conf the I thought 'what if I shared it again , then deselected sharing and pressed the modify share button' so I did and it worked. Here is a screenshot of what I had before if anyone has seen anything similar.

---

### Post by llawwehttam on 2010-01-26
Bug report is here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/512867](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/512867)

---

### Post by Morbius1 on 2010-01-26
That's a known bug in nautilus-share. It's considered minor because it doesn't actually stop sharing it simply reports in nautilus that it's not shared. I don't consider that minor but that's my opinion.

The only way to know whether a folder is shared or not is to open a terminal and type: **net usershare info**

You can, BTW, delete a nautilus-share from the terminal:
**net usershare delete sharename**

For those suggesting going into smb.conf, the shares are not defined in smb.conf using nautilus-share. It's defined in /var/lib/samba/usershares.

---

### Post by mathewd on 2011-07-18
i had the same issue as Morbius1. i don't feel that it's minor at all; i realised that folders i had assumed (and that in natilus appeared to be) unshared were in fact still being shared on the windows network. as a comfortable-only-in-GUI linux user :P this bothered me a bit.

anyway, i wanted to point out that ***/etc/samba/smb.conf*** held the share entries for those folders i shared via the Samba application (GUI version from software centre), while ***var/lib/samba/usershares*** contained the entries for those i shared via Nautilus. and each did not display the shared of the other.

this is probably basic info for you guys; just added this for other newbies like myself :) anyway so glad i found this thread, as your advice solved my problem too! thanks so much!!!!!

---

