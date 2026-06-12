---
title: "acer aspire one netbook"
date: 2009-09-06
forum: General Help
---

### Post by TheFuzz4 on 2009-09-06
So I just bought my wife a netbook today and me being the buntu lover I am (I run kubuntu on both my lappy and desktop's) I decided that I would install the netbook remix of Ubuntu on this today.  I never let it boot up into Windows once :).  Anyways I have two questions for the group today.
1. I am wondering if maybe this is something specific with the model but when I close the lid it does not go into standby and I'm not sure if it just doesn't know that the lid is closed because her Mom also has one of these and it does the same thing.
2. Ok I know how to do this with command line and everything but since this is my wife's first interaction with linux I know that she will be very upset if she has to go to a command line to do this each time.
I have 2 windows network shares that need to be mounted on startup.  Normally I just put this in the fstab and for my laptop I just punch in the mount -a to mount them after the wireless is connected but as I said this isn't really an option for my wife is there a way in Ubuntu to have it mount these shares like on log in or after the network is connected?

Thank you all in advance for your assistance with this.

---

### Post by fooman on 2009-09-06
i use samba and i have my shares mount at bootup by adding them to places > connect to server

for service type, choose "windows share"
for server,  type in the ip address assigned by your router (192.168.*.*) of the machine that holds the shares.
fill in the other information in the spaces provided...then put a check next to "add bookmark".  give it a name of your choice and click "connect".
you should be prompted for your password...type it in. 
if you like, you can choose to have it remember the password forever and you won't have to type it in every time you wish to access the shares.

the shares should show in places > bookmarks after rebooting.

i did not have to make any edits to fstab and it mounts at boot for me.  hope that helps.

---

### Post by TheFuzz4 on 2009-09-06
Thank you very much.  I think that the fstab stuff is mainly for the kubuntu side of the house that I normally hang out in.  This is really my first major exposure to Ubuntu

---

### Post by fooman on 2009-09-06
sorry,  for netbook remix...in the top left, click the main menu, then > places > connect to server

then follow as i described above.  after rebooting,  the shares should show in the right side of the screen on the ubuntu netbook remix's desktop.

---

