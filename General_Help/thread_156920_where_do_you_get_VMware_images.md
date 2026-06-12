---
title: "where do you get VMware images?"
date: 2006-04-08
forum: General Help
---

### Post by threethirty on 2006-04-08
I was wanting to run windows in linux (its an elistist thing:) ).  I got the VMwarePlayer installed, and now i need an image.  

And I was also wondering how to start it these were my best guesses:
```
three@CondorV2:~$ vmware
bash: vmware: command not found
three@CondorV2:~$ wareplayer
bash: wareplayer: command not found
three@CondorV2:~$ vmplayer
/usr/bin/vmplayer: line 85: /etc/vmware/locations: No such file or directory
/usr/bin/vmplayer: line 177: /lib/wrapper-gtk24.sh: No such file or directory
/usr/bin/vmplayer: line 177: exec: /lib/wrapper-gtk24.sh: cannot execute: No such file or directory
three@CondorV2:~$ vmwareplayer
bash: vmwareplayer: command not found
three@CondorV2:~$

```

I have a copy on WinXP Pro do i need that at all?

thanks in advance

---

### Post by scooper on 2006-04-08
I would guess you need access to a full copy of VMware to create an image for the player.  Someone has to format the virtual disk and install something.  Probably only possible on an uncrippled product.  I'm just guessing.

It seems VMware offers some canned images for your amusement.

[http://www.vmware.com/vmtn/appliances/browserapp.html](http://www.vmware.com/vmtn/appliances/browserapp.html)
[http://www.vmware.com/vmtn/appliances/](http://www.vmware.com/vmtn/appliances/)

Enjoy.
Steve

---

### Post by arkangel on 2006-04-09
by having the vmplayer you can build images  directly  , there is  a method to do it
[http://ubuntuforums.org/showthread.php?t=84275&highlight=windows+xp+install](http://ubuntuforums.org/showthread.php?t=84275&highlight=windows+xp+install) 

but you can go the vmware home site and download the  workstation  for evaluation  

once  you have the vmware workstation , in the main menu , create new image (xp or any other system)  and start the machine , just there insert your cd  and install as  you would  do normally with XP  ,
 when your image is complete, you can erase the vmware workstation and  use the free player from 
vmware.com

---

### Post by NiN on 2006-04-09
another tip:
vmware-server is free to download too!
With that you can do everything like with the player, but also create images and a lot of neat stuff.
have fun :)

---

### Post by Prospero2006 on 2006-04-09
Do Not Post Helpful Comments That Involve Pirating Software. 

Thanks.

-zenwhen

---

### Post by NiN on 2006-04-10
I was not talking about pirating...

have a look yourself

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

---

### Post by taurus on 2006-04-10
Or install qemu with apt-get and read the doc from here on how to set it up, [http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)...
```

sudo apt-get install qemu

```

---

