---
title: "can not login ubuntu"
date: 2010-10-28
forum: General Help
---

### Post by guoyunsky on 2010-10-28
Deal All:
i use Ubuntu10.04 .
Today i want to update Python version,so i removed python first(use command:sudo apt-get remove python ).then i found some problems:
1.i can not login Ubuntu desktop ,only can login safe mode(by ALT+F1).and there is a prolem:[COLOR=red]Ubuntu is running in low-graphics mode[/COLOR]
2.then i use ALT+F1 to login safe mode,and i want use commad to resolve or repair system.but when i login successfully,the console reports:
[COLOR=red]Last login: Sat Jun 19 08:01:00 EDT 2010 on ttyS0[/COLOR]
[COLOR=red]exec: 3: /usr/lib/update-notifier/update-motd-cpu-checker: not found[/COLOR]
[COLOR=red]run-parts: /etc/update-motd.d/20-cpu-checker exited with return code 2[/COLOR]
[COLOR=red]run-parts: failed to stat component /etc/update-motd.d/50-landscape-sysinfo: No such file or directory[/COLOR]
[COLOR=red]exec: 3: /usr/lib/update-notifier/update-motd-updates-available: not found[/COLOR]
[COLOR=red]run-parts: /etc/update-motd.d/90-updates-available exited with return code 2[/COLOR]
[COLOR=red]exec: 3: /usr/lib/update-notifier/update-motd-reboot-required: not found[/COLOR]
[COLOR=red]run-parts: /etc/update-motd.d/98-reboot-required exited with return code 2[/COLOR]
 
[COLOR=red][COLOR=#000000]3.i use these commands to resolve problem 2:[/COLOR][/COLOR][COLOR=red]
[COLOR=red][COLOR=red]sudo dpkg --configure -a[/COLOR]
[COLOR=red]sudo apt-get -f install[/COLOR]
[COLOR=red]sudo apt-get --fix-missing install[/COLOR]
[COLOR=red]sudo apt-get update[/COLOR]
[COLOR=red]sudo apt-get dist-upgrade[/COLOR]
[COLOR=red]sudo apt-get clean[/COLOR]
[COLOR=red]sudo apt-get autoremove[/COLOR]
[COLOR=red]sudo apt-get update[/COLOR]
[COLOR=red]sudo apt-get install ubuntu-desktop[/COLOR]
[COLOR=red]sudo reboot[/COLOR]
but no result.
 
4.i want to repair system,use these commands:
[FONT=Courier New][COLOR=red]sudo -i[/COLOR][/FONT]
[FONT=Courier New][COLOR=red]fdisk -l[/COLOR][/FONT]
[FONT=Courier New][COLOR=red]mount /dev/sda9 /mnt[/COLOR][/FONT]
[FONT=Courier New][COLOR=red]grub-install --root-directory=/mnt /dev/sda[/COLOR][/FONT]
[FONT=Courier New][COLOR=red][COLOR=black]but it will report this error:[/COLOR][/COLOR][/FONT]
[FONT=Courier New][COLOR=red]/usr/bin/python: can't find '__main__.py' in '/usr/share/command-not-found'[/COLOR][/FONT]
 
[/COLOR][COLOR=black]i am sorry for my bad ubuntu and my bad english,and i use it for a short time,please help me!thank you very much[/COLOR]
 
[/COLOR]

---

### Post by sisco311 on 2010-10-28
Hi and welcome to the forums!

python is an essential part of Ubuntu, a lot of packages are depending on it, so you should never uninstall it. python 3.1.2 is in the repositories, you can safely install it alongside the version Ubuntu uses.  

Assuming that "sudo apt-get -f install" fixed the broken packages and you have a working internet connection, run:
```
sudo apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop
```

The above command will install any packages that are installed by default in an Ubuntu installation.

Good luck!

---

### Post by guoyunsky on 2010-10-28
> **sisco311 said:**
> Hi and welcome to the forums!
 
python is an essential part of Ubuntu, a lot of packages are depending on it, so you should never uninstall it. python 3.1.2 is in the repositories, you can safely install it alongside the version Ubuntu uses. 
 
Assuming that "sudo apt-get -f install" fixed the broken packages and you have a working internet connection, run:
```
sudo apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop
```
 
The above command will install any packages that are installed by default in an Ubuntu installation.
 
Good luck!
 
Thank you for your reply.but Ubuntu continue can not login after i run your command.
any other command what i have not ran?

---

### Post by sisco311 on 2010-10-28
> **guoyunsky said:**
> Thank you for your reply.but Ubuntu continue can not login after i run your command.
any other command what i have not ran?

Well, you need to provide more information. Try to explain in details why you can't log in, _post the error messages_ and so on...

---

### Post by guoyunsky on 2010-10-28
> **sisco311 said:**
> Well, you need to provide more information. Try to explain in details why you can't log in, _post the error messages_ and so on...
 
i input a error command(rebooot), it report this error:
[FONT=Courier New][COLOR=#ff0000]/usr/bin/python: can't find '__main__.py' in '/usr/share/command-not-found'[/COLOR][/FONT]

[FONT=Courier New][COLOR=black]but i run command:python,it can login python console,and can run python program.[/COLOR][/FONT]

[FONT=Courier New]and i run command:which is python,result like this:[/FONT]
[FONT=Courier New][COLOR=red]/usr/bin/python[/COLOR][/FONT]

[FONT=Courier New][COLOR=black]then i run command:whereis python,result like this:[/COLOR][/FONT]
[FONT=Courier New][COLOR=red]/usr/bin/python /usr/bin/python2.6 /usr/bin/python2.6-config /etc/python /etc/python2.6 /usr/lib/python2.6 /usr/lib/python3.1 [/COLOR][/FONT]
[FONT=Courier New][COLOR=red]/usr/local/lib/python2.6 /usr/local/lib/python2.6 /usr/include/python2.6[/COLOR][/FONT]
[FONT=Courier New][COLOR=red]/usr/share/python ...[/COLOR][/FONT]
[FONT=Courier New][COLOR=black]there are two versions Python.and i am sure thaht python is installed successfully[/COLOR][/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]then i ready to login ubuntu:[/FONT]
[FONT=Courier New]1)i can not login the desktop of Ubuntu,and will report error like this:[/FONT]
[FONT=Courier New] [FONT=Verdana][COLOR=#ff0000]Ubuntu is running in low-graphics mode[/COLOR][/FONT][/FONT]
[FONT=Courier New][FONT=Verdana][COLOR=black]2) and it can not login desktop.it always stops in the login screen.then i use ALT+F1 to login the safe model.ant it reports this error,but i can use the command to operate Ubuntu:[/COLOR][/FONT][/FONT]
[FONT=Courier New][FONT=Verdana][COLOR=#ff0000]Last login: Fri Oct 29 10:01:00 EDT 2010 on tty1[/COLOR][/FONT][/FONT]
[FONT=Courier New][FONT=Verdana][COLOR=red]/etc/update-motd.d/00-header: 4 lsb_release: not found
exec: 3: /usr/lib/update-notifier/update-motd-cpu-checker: not found
run-parts: /etc/update-motd.d/20-cpu-checker exited with return code 2
exec: 3: /usr/lib/update-notifier/update-motd-updates-avaible: not found
run-parts: /etc/update-motd.d/90-updates-avaible exited with return code 2
exec: 3: /usr/lib/update-manager/release-upgrade-motd: not found
run-parts: /etc/update-motd.d/91-release-upgrade exited with return code 2
exec: 3: /usr/lib/update-notifier/update-motd-reboot-required: not found
run-parts: /etc/update-motd.d/98-reboot-required exited with return code 2[/COLOR][/FONT][/FONT][FONT=Courier New][FONT=Verdana][/FONT][/FONT]
[FONT=Courier New][/FONT] 

[FONT=Courier New]and any other informations of my computer what you want to know?please tell me ,thank you ![/FONT]

---

### Post by sisco311 on 2010-10-29
Do you get any error message when you run:
```
sudo apt-get install ubuntu-minimal ubuntu-standard ubuntu-desktop
```?

---

