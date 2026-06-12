---
title: "Another sudo problem?"
date: 2006-05-29
forum: General Help
---

### Post by Hoffmann on 2006-05-29
Hello:

I am having problems in reading/writing my /etc/sudoers file. When I try to read it with the command: 

sudo gedit /etc/sudoers

I get the error:

sudo: /etc/sudoers is mode 0640, should be 0440

Now, I cannot open any applications that needs me as a sudo user...

Please, help!
Thanks!

---

### Post by johannes on 2006-05-29
I think you have to use the command "sudo visudo", which will open /etc/sudoers in the editor "vi". Read about vi commands [here.]("http://www.groovyweb.uklinux.net/?category=linux&page_name=how%20to%20use%20vi")

---

### Post by Hoffmann on 2006-05-29
[QUOTE=johannes]I think you have to use the command "sudo visudo", which will open /etc/sudoers in the editor "vi". Read about vi commands [here.]("http://www.groovyweb.uklinux.net/?category=linux&page_name=how%20to%20use%20vi")[/QUOTE]

The problem is that sudo is not working anymore. How could I change its permission, or fix this problem?

---

### Post by johannes on 2006-05-29
Ok... Can you switch to root with "su"? If you can, try: 

chmod 0440 /etc/sudoers

Otherwise, you should be able to change the permissions using a Live CD.

---

### Post by aysiu on 2006-05-29
Boot into recovery mode, and you'll be root.

---

### Post by Hoffmann on 2006-05-30
[QUOTE=aysiu]Boot into recovery mode, and you'll be root.[/QUOTE]
I just solved my problem. I reinstalled Dapper. I think the problem was the live-CD.
Of course, all will be ready for the final version.
The conclusion is: no system is perfect.
Any way, I am a Ubuntu fan. ;)

---

