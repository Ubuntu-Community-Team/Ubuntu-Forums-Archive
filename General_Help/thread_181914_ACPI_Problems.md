---
title: "ACPI Problems"
date: 2006-05-25
forum: General Help
---

### Post by lanaki69 on 2006-05-25
Ok here goes, I am new to Ubuntu. I tried to install Ubuntu on a Compaq Proliant PIII 600Mhz/512MB/Compaq 2DH Controllerw/ Raid 0(1x18gb, 4x9.1gb).
I get the follwing errors...:evil: 
Unable to locate RSDP
Loading...
Fatal Error Inserting Fan
Fatal Error Inserting Thermal
Alert /dev/ida/c0d0p1 does not exist - Dropping to a shell
/bin /sh can't access tty; job control turned off

I would like to know how to setup this server to use Unbuntu but I can't figure out how to disable ACPI and APM.:confused: 

Any help would be greatly appreciated!:D

---

### Post by nanotube on 2006-05-25
at the boot prompt, instead of jsut hitting enter, type in "linux acpi=off" and then enter.

---

### Post by lanaki69 on 2006-05-25
Didn't help. I think it needs to know where the /dev/ida/c0d0p1 is. Now if I only knew where and how to change the startup location. arrgghh!  Might need to go back to Microsoft Server 2003.  Any Ideas?  :confused:

---

### Post by hiikeeba on 2006-06-03
My employer just replaced their web server and let me have the old one.  500MHz P3 with 512 MB of ram.  Tried to boot from the 6.06 cd and it stopped.  Tried "linux acpi=off" and install hangs at "Adding live CD user." I can't even get the darn thing to boot into Windows Server 2000.

---

