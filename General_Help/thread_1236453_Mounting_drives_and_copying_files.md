---
title: "Mounting drives and copying files"
date: 2009-08-10
forum: General Help
---

### Post by M4D88 on 2009-08-10
Hi Guys, 

what commands do i use to make my ubuntu mount a drive and copy files during boot up from a drive thats already mounted to the newly mounted drive?, then shutdown the PC

I guess i need to write a boot script, how and what commands to i use to do this?

The files im copying are replaceing exsisting file names, so will i be prompted to overwrite?
If so, I need the process to be fully automated (and yes i know the pc will just boot up and shut down every time its turned on) 

Cheers

---

### Post by Elv13 on 2009-08-10
Mount command = mount
copy command = cp
shutdown command = shutdown -i or halt

Mounting a driver with mount on it will not work, if it is on a remote computer, you can use scp with ssh.

---

