---
title: "trouble installing ubuntu (wubi-10.04)"
date: 2010-05-27
forum: General Help
---

### Post by Kayothic on 2010-05-27
I tried a few times now even tried reinstalling the installer and such and keep getting this error (taken from Wubi-10.04-rev189.log, closed the actual error message)
 
File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.
The system cannot find the file specified.
 
>>stdout=
05-27 21:12 DEBUG TaskList: New task modify_bcd
05-27 21:12 DEBUG TaskList: ## Finished modify_bootloader
05-27 21:12 DEBUG TaskList: # Finished tasklist
 
 
This is happening at the end of the installation, something about it not being able to find something. I already have ubuntu 9.10 on my lappy dual booted with windows (and of course since I';m using wubi I am using windows, I am doing this one because I just cant get my other one to connect to the internet :P)
 
I would really like to get this on and working, and if anyone could please help me that would be greatly appreciated :D!
 
oh and I don't have a usb of 4 gb (lost it, tried ipod as it but it didn't work), and also don't have a 4gb RW CD :P
 
thanks
 
~Kayothic

---

### Post by Kayothic on 2010-05-28
I again tried this with writing a CD (found one and it worked and everything, used infra recorder and it worked great.) but at 48% of the installation it said something may be wrong with the disc and abortted :<
 
any help?

---

