---
title: "Removing Ubuntu 10.10"
date: 2010-11-05
forum: General Help
---

### Post by kadak.chocho on 2010-11-05
I have a sony viao netbook with 5 partitions.
the first one is vista loader - Factory setting restore.
the second one is windows, the third one is ubuntu remix 10.10 and the forth is swap.
There is also a 100MB partition.

Now, i have exchange my netbook with a faster, newer laptop/Desktop.
So i need to restore the sony netbook to its original setting.
I do not have a windows CD or a CD drive for that matter.

I tried to run the prog to restore, but it needs to restart quite a few times .... and each time i get the 'grub-rescue>' prompt.

Now ... sadly .... i have a netbook with the grub and no windows or ubuntu .... and the only thing at my disposal is the ubuntu remix 10.10 boot USB stick.

---

### Post by Quackers on 2010-11-05
Welcome to UF.
Do you know how to access the hidden recovery partition? It will be something like tapping the F11 key or the del key during boot. Try restoring the system that way.

---

### Post by kadak.chocho on 2010-11-06
I tried recovering using that.
The key was F10. And that was my mistake. IT formated the ubuntu and wondows partitions and tried to join them. However, the grub still remains. I think i will need to buy a CD drive .. :( ... and a Windows CD too.

---

### Post by P4man on 2010-11-06
You should be able to restore the windows bootloader form an usb stick. Google around for BartPE. Hopefully that will let you access the recovery partition again and reset the machine to factory status.

If not, Id think twice about paying for another windows license. You already paid one. Borrow an installation cd, put it on a usb stick and install it with your key.

---

### Post by Rody on 2010-11-06
get a buddy with win7 to make you a rescue disk, boot from that and find the option that gets you to the command prompt.

bootrec.exe /fixmbr i think should fix you up.

there are a couple of other commands to try if that does not work, just type in bootrec and it should  tell you all the commands you can try.

---

### Post by kadak.chocho on 2010-11-18
Thank you all ... i found a way to solve the problem

---

### Post by Mark Phelps on 2010-11-18
Given the enormous variety of the solutions proposed to you -- it would be really useful to the community if you told us HOW you solved this.  Please??

---

