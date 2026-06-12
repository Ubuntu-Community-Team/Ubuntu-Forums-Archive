---
title: "Problems with online Netbean installation persists."
date: 2011-11-10
forum: General Help
---

### Post by Randy Schilling on 2011-11-10
Hello - 

I've had a tremendous amount of help from this forum over the past several days.
 My system would not look as good as it does without the generous help of the people of this forum.  
 I've had so much help, help was so immediate, I hope I haven't abused the
 privilege of membership in this forum (This post being identical to a 5 hour old  post 
 that received no attention under another category).  
 
I want to set up the Netbeans IDE under my new Ubuntu 11.10 system.  
I could not find a selection for it in either the Ubuntu Software Center or Synaptic
so I went to the Netbeans website.  If this is not the way to proceed then please let me know.

I followed the instructions to install
        Java SE Development Kit 6 Update 29 and NetBeans IDE 7.0.1 Software Bundle
 at[ http://www.oracle.com/technetwork/ja...91-177131.html]("http://www.oracle.com/technetwork/java/javase/downloads/install-jdk6-22nb691-177131.html")
 The main instruction therein is to download a file, make it executable,  move to the appropriate  directory and enter the command:      ./jdk-6u29-nb-7_0_1-linux-ml.sh.
I did so as a superuser (having entered sudo su) and the system's response was this:
 
 Configuring the installer...
 Searching for JVM on the system...
 Preparing bundled JVM ...
 Extracting installation data...
 Running the installer wizard...
 
 All this appeared in my bash terminal and there was no sign of an installation wizard.  
Something is wrong and I don't know what to try next.  Any help would be most sincerely 
appreciated.  


Thanks so much  - Randy

---

### Post by Foxheadz on 2011-11-10
Im not familiar with the programs but i would try following this [https://help.ubuntu.com/community/Netbeans](https://help.ubuntu.com/community/Netbeans)

---

### Post by Randy Schilling on 2011-11-11
Hello and thanks.  The Ubuntu-Community-Netbeans webpage is quite dated, 
curious that it bemoans Synaptic as out-of-date.
Your Google tip falls nothing short of a revelation - Thanks.  

What works to install Netbeans to Ubuntu is the following three step process.
   1. Make sure your Java is up-to date at [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp).
    2. Install JDK from [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html).
   3. Install Netbeans from [http://netbeans.org/downloads/index.html](http://netbeans.org/downloads/index.html)
I found the instructions provided by Oracle and its community to be up-to-date, detailed and top-to-bottom.
Use them with the following clarifications. 
The instructions for Java suggest that removal of existing Java is necessary; that seems to be true for Windows but not Linux.
The Netbeans instructions include the url to the JDK installation.  
You'll have to create directories for Java and JDK.  
I created /user/local/java and /usr/local/jdk7.
The Netbeans installer at first did not find my jdk;  I manually entered /usr/local/jdk7/jdk1.7.0_01.
When my installation completed, I went to Dash (under my beautiful new Ubuntu 11.10) searched Netbeans, 
found it, clicked it and it exploded onto my desktop.
I tested my installation by running the Welcome sample under C++/C.
I mclicked (menu click) its icon in the launcher and clicked Keep in launcher.  
I moved its icon to the top of my launcher's panel.
My original plan was to combine steps 2 and 3 and install the JDK + Netbeans bundle.  
That failed under Ubuntu (as described in an earlier post) but it works under Windows.
This should relieve any would-be developer of some tense guessing.

---

