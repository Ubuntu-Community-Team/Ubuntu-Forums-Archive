---
title: "How do you remove or delete files Ubuntu 9.04"
date: 2009-10-26
forum: General Help
---

### Post by Elliptic on 2009-10-26
Ok, sorry for this, but I am learning and new to Ubuntu.  So I figured out the SFTP and connected via Dreamweaver.  However I "put" files under a directory I did not want.  So I created the /var/www/*mysite* folder, gave my user permissions to that folder and it is linking up with Dreamweaver.  
 
My Question... no I have those same files in two different places on my Server.  So how do I go back in there and remove them safely... (there are a lot of pictures that uploaded and taking up a lot of room).
 
What is the code I need to type?
 
:p

---

### Post by Primefalcon on 2009-10-26
> **Elliptic said:**
> Ok, sorry for this, but I am learning and new to Ubuntu.  So I figured out the SFTP and connected via Dreamweaver.  However I "put" files under a directory I did not want.  So I created the /var/www/*mysite* folder, gave my user permissions to that folder and it is linking up with Dreamweaver.  
 
My Question... no I have those same files in two different places on my Server.  So how do I go back in there and remove them safely... (there are a lot of pictures that uploaded and taking up a lot of room).
 
What is the code I need to type?
 
:p
for file
rm <filename>

for multiple files
rm <file1> <file2> <so on>

for a folder and everything in it
rm -R <folder name>

for just an empty folder
rmdir <folder name>

for memory -R just stands for Recursive

---

### Post by Giblet5 on 2009-10-26
rm = remove file(s)
rmdir = remove folder(s)

The combination "sudo rm..." will delete anything and everything, and can easily force you to reinstall. Don't use that form unless you know 100% what you're doing, where you're doing it, and what the expected result will be.

---

### Post by Elliptic on 2009-10-26
Awesome guys,  that is what I needed to know.  Thank you for the heads up on deleting to cause a reload.  I created a /home/*user*/www/*mysite* file location and cannot get my virtual names to resolve to this location, so I read in many places over the forums to just give myself permission under the /var/www/ section and create /var/www/*mysite *then point my VirtualHost DirectoryRoot to that folder.  I have done that, but now running into permissions deal, I think.
 
Basically, I am trying to set up my server to Host two websites on one Static IP address and one server.  I have a lot to learn cuz I cannot get it to work.  When I open my browser on my Window laptop, I get the follwoing:
 
**Index of /**

[IMG]http://www.silverlakesavannahs.com/icons/blank.gif[/IMG][Name]("http://www.silverlakesavannahs.com/?C=N;O=D")[Last modified]("http://www.silverlakesavannahs.com/?C=M;O=A")[Size]("http://www.silverlakesavannahs.com/?C=S;O=A")[Description]("http://www.silverlakesavannahs.com/?C=D;O=A")
Apache/2.2.11 (Ubuntu) Server at [www.silverlakesavannahs.com](www.silverlakesavannahs.com) Port 80

---

