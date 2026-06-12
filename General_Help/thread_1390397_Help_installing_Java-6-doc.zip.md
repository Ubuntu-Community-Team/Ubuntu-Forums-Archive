---
title: "Help installing Java-6-doc.zip"
date: 2010-01-25
forum: General Help
---

### Post by TrompStomp on 2010-01-25
Hi there. I am trying to install the java docs in ubuntu 9.10. My problem is when I go to Suns website [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/) to download the jdk-6-doc.zip (as directed by synaptic), the only file I can find to download is the jdk-6u18-docs.zip which is located under the "Java SE Documentation" link.

I assume I am just missing it but I have looked for some time now and I am having no luck. Could someone point me in the right direction or is there another way to install this? Thanks in advance!!

---

### Post by cariboo on 2010-01-25
Have you checked to see if the documentation is installed by looking in /usr/share/doc, if it is just documentation, it won't create a link on the desktop.

---

### Post by TrompStomp on 2010-01-26
I have figured out a solution. In case anyone else is having problems with this...

1) Download the file jdk-6u18-docs.zip from Suns website.
2) Rename jdk-6u18-docs.zip to jdk-6u10-docs.zip 
3) Move the file jdk-6u10-docs.zip to your /tmp directory  
4) Change ownership of the file /tmp/jdk-6u10-docs.zip to root:root
5) Install sun-java6-doc through synaptic

 Hope this helps someone else.

---

### Post by Publicspoon on 2010-01-27
I am trying to download the new version of java, because from the ubuntu software program i can only download version 6.  The current version is 6 update 8, but i followed the instructions ( but i dont know if i have to download the 32 bit or not or what an rpm is)  so i downloaded the Linux self extracting file.  Website for downloading java update--[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp).  I get to the part of the instructions to where (number 3). 
 
[http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting) web site to the directions
 
Change to the directory in which you want to install. Type:
**cd <directory path name**
 
I do that but tells me that the password is wrong.  Says my root password is wrong.  But i am the admin for this computer.  Dont know what to do please advise.  
 
sal

---

