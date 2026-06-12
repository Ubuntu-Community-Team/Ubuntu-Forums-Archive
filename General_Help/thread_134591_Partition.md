---
title: "Partition"
date: 2006-02-22
forum: General Help
---

### Post by playmobiel on 2006-02-22
Hi there ,

I have 3 hd in my pc , now one is the /usr , the other one /home and the other one the root. I would like to clear one hd for another OS , but i don't know how to do this , i would like to clear the /usr partition , i think i must copy the /usr to the root hd , but how do i do this?

---

### Post by Ramses de Norre on 2006-02-22
I guess /usr is a mountpoint for that hd then? I should copy everything to a folder under /, delete the mountpoint and rename the new folder to usr.
Make sure the new folder looks like it is the old mountpoint.

---

### Post by lamego on 2006-02-22
I would do something lile this:
```

# Create the directoty that will get a copy of /usr
mkdir /usr2
cd /usr
# Do the copy using tar to preserver symlinks if any
tar cvf - . | tar -C /usr2 -xvf -

```
At this stage you will need to unmount the current /usr, probably you will need be able to do it because it is in use, reboot into single user mode.
Booting in single user mount, edit your /etc/fstab, and remove the /usr entry then
Rename your usr2 to usr with:
  mv /usr2 /usr
Reboot, everything should be fine now.

---

### Post by playmobiel on 2006-02-22
Thanks for fast and usefull replys , i still have one question, how do i boot in single user mode? :) 

Thanks

---

### Post by Ramses de Norre on 2006-02-22
In grub choose recovery mode, or type sudo init 1 in a terminal.

---

### Post by playmobiel on 2006-02-22
Thanks , i'll try that

---

