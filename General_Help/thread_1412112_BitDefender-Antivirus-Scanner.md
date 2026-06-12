---
title: "BitDefender-Antivirus-Scanner"
date: 2010-02-20
forum: General Help
---

### Post by Richiegs on 2010-02-20
Hi, I am using Ubuntu 9.10 and I want to download BitDefender Antivirus Scanner for Unices. Nevertheless, BitDefender Antivirus Scanner for Unices has many different versions, such as 
1. BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run
2. BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run.md5
3. BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run
4. BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run.md5
5. BitDefender-Antivirus-Scanner-nogui-7.6-4.linux-gcc3x.i586.deb.run
6. BitDefender-Antivirus-Scanner-nogui-7.6-4.linux-gcc3x.i586.deb.run.md5

Which one should I download?

Thank you

---

### Post by Richiegs on 2010-02-20
One more thing, I am using 32 bit.

---

### Post by switch10 on 2010-02-20
I assume you will want a GUI.  So you want one of the first one's.  AMD64 is for a 64 bit processor, so that rules that out as well.  An MD5 sum is a number to check that the download is correct.  The one you want is:  3. BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run

---

### Post by iamwhatiseem on 2010-02-20
Why do you want Antivirus?
Do you run everything in root or something?

---

### Post by switch10 on 2010-02-20
> **iamwhatiseem said:**
> Why do you want Antivirus?
Do you run everything in root or something?

maybe he wants to run it on a Windows partition.

---

### Post by jimmers on 2010-02-21
Try this I 32 bit jaunty, and have this installed,

  	 	 	 	 	 	  
[LIST]
[*][BitDefender]("https://help.ubuntu.com/community/BitDefender?action=fullsearch&context=180&value=linkto%3A%22BitDefender%22") 		
[/LIST]
 ** What is BitDefender ?**

  BitDefender is a program to check for Windows viruses and malware. It can be run in the background or on demand when required. Once installed it can be found under Applications - Systems Tools. It can be used as an alternative to clamav/clamtk.  
 **Installation**

  Add the repository by going to System - Administration - Software Sources, click on the 'Third Party Software' tab. Now click on 'Add' and enter  
 deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free  Click on 'Close' and press 'Reload' when prompted. Ignore the 'No repository key' error (if displayed). Now in Applications - Accessories - Terminal add the repository key:  
 wget [http://download.bitdefender.com/repos/deb/bd.key.asc](http://download.bitdefender.com/repos/deb/bd.key.asc) sudo apt-key add bd.key.asc  Now update the apt cache with  
 sudo apt-get update  Install the graphical interface and command line program with  
 sudo apt-get install bitdefender-scanner-gui Once complete you now need to log out and log back in again. a menu shortcut will be generated (Applications - System Tools - BitDefender Scanner).  
 Before running the scanner it's probably best to install the latest virus/malware signatures by clicking on the 'Update' button.

---

### Post by Richiegs on 2010-05-07
> **jimmers said:**
> Try this I 32 bit jaunty, and have this installed,

                                 
[LIST]
[*][BitDefender]("https://help.ubuntu.com/community/BitDefender?action=fullsearch&context=180&value=linkto%3A%22BitDefender%22")
[/LIST]
 ** What is BitDefender ?**

  BitDefender is a program to check for Windows viruses and malware. It can be run in the background or on demand when required. Once installed it can be found under Applications - Systems Tools. It can be used as an alternative to clamav/clamtk.  
 **Installation**

  Add the repository by going to System - Administration - Software Sources, click on the 'Third Party Software' tab. Now click on 'Add' and enter  
 deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free  Click on 'Close' and press 'Reload' when prompted. Ignore the 'No repository key' error (if displayed). Now in Applications - Accessories - Terminal add the repository key:  
 wget [http://download.bitdefender.com/repos/deb/bd.key.asc](http://download.bitdefender.com/repos/deb/bd.key.asc) sudo apt-key add bd.key.asc  Now update the apt cache with  
 sudo apt-get update  Install the graphical interface and command line program with  
 sudo apt-get install bitdefender-scanner-gui Once complete you now need to log out and log back in again. a menu shortcut will be generated (Applications - System Tools - BitDefender Scanner).  
 Before running the scanner it's probably best to install the latest virus/malware signatures by clicking on the 'Update' button.

I tried to run those instructions from the terminal, but it did not work. Do you mind to write out the instructions step by step? Thanks

---

### Post by Aco2 on 2010-05-08
Which one should you download ? not sure, but go to [trust download website]("http://www.trustdownload.com") and download some versions, not sure what version will work for you, I use 'BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run.md5'.

---

### Post by Aco2 on 2010-05-08
But I believe you don't need BitDefender Antivirus Scanner on ubuntu.

---

