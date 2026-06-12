---
title: "GRUB module not found after restart"
date: 2010-06-04
forum: General Help
---

### Post by yarri on 2010-06-04
Hej!

I have ubuntu 10.04 running on HP Pavilion laptop and I have a dual boot with windows XP. 
The kernel
```
uname -r
2.6.32-22-generic

```
When I restart it, or change to Windows XP the computer does not boot. Instead I get a message: 
```
module name not found, press any key 
```(ore something to this effect).
I can repair it using live cd but I have no idea what is causing this problem. 
```
sudo grub-install --recheck --root-directory=/media/10c7e47f-2192-4ce4-9ad3-80069abbe81a/ /dev/sda 
```

Does anyone know what is causing this problem and if there is anything to that can fix it?

---

### Post by art20 on 2010-07-11
I have this exact problem, after installing Ubuntu 10.4 I can restart as many times as I want as long as I dont log into windows 7 (64bit). If I do that, the next time I restart I get the "module not found" message.

I havent been able to fix this without deleting the ubuntu partition and logging back into windows using the install cd.

If you know a better way to fix the issue I'd appreciate it a lot if you posted it here.

---

### Post by nowtejas on 2010-09-19
I also have the same problem on my Dell Studio XPS 1645 laptop running Kubuntu 10.04 dual booting with Windows 7 Ultimate 64 bit.

While I do not have a "permanent" solution, so far, everytime I get the "Module not found" message, I put in the Kubuntu Live CD.

and go to Terminal in the LiveCD Environment.

and then following commands:

1) mount the disk where I want to install the GRUB ( in my case root partition of kubuntu is sda6 where I want the grub to be.
```
sudo mount /dev/sda6 /mnt/
```

2) install the GRUB in the location that we just mounted. and give a link to that from the MBR ( MBR being located in /dev/sda )
```
sudo grub-install --root-directory=/mnt/ /dev/sda/
```

3) Reboot, and voila GRUB is back, BUT, we have to update it to be used without the live CD, so, boot into Linux and open terminal again, and, 
```
sudo update-grub
```

and that's it..
the grub should be back and stay until we boot into windows next time.

---

### Post by xircon on 2010-09-19
Permanent solution - remove and uninstall Dell Datasafe, it modifies the MBR.  You will of course have to reinstall grub one more time :)

---

