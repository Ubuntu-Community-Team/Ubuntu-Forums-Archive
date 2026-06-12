---
title: "Administrator default password ???"
date: 2006-04-15
forum: General Help
---

### Post by gharz on 2006-04-15
hi, guys.

i need ur help coz i'm a newbie.

i'm trying to install java and i need the administrator password because i'm using the "su" command. i don't remember making a password for the administrator during the installation. i'm using ubuntu breezy.

can you help me please what the default password for Administrator is for su?

awaiting for help.

---

### Post by PriceChild on 2006-04-15
use
```
sudo passwd root
```
To set the password, 

use 
```
[FONT=verdana,geneva,lucida,'lucida grande',arial,helvetica,sans-serif]s[/FONT]udo passwd -l root
```
To remove it when done.

---

### Post by Ensnared on 2006-04-15
Ubuntu doesn't have an administrator password by default. The way you would normally do things with root (e.g. administrator) privileges is by using the "sudo" command, which only requires you to enter your own password.

If you do need to log in as root instead, you can set a password for root using this command:
```
sudo passwd root
```
You'll then first enter your password, then enter the password you want for root, and confirm the password. When this is done you'll be able to log in as root, or use "su" to become root.

---

### Post by Ramses de Norre on 2006-04-15
> use

sudo passwd -l root

To remove it when done.sudo passwd -l root will lock the root password and you wont be able to go into recovery mode as root.
In order to go back to the default situation you need to do sudo gedit /etc/shadow, search the line for root and make it look something like this: ```
root:*****:13187:0:99999:7:::

```The * will be replaced by an encrypted passwd and you need to set it back to *. Don't change the other numbers.

---

