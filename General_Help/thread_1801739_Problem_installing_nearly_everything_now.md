---
title: "Problem installing nearly everything now"
date: 2011-07-11
forum: General Help
---

### Post by semt0x on 2011-07-11
Hi    I have been running Ubuntu for nearly 2 weeks now and I was able to install using the terminal as well as the software centre..   I have started to have a problem installing anything now for instance I'm putting this code into the terminal of BT5 but exactly the the same error is occurring on the Ubuntu terminal as well and it does it for any package not just crunch.. I'm guessing this is to do with drive E: right?       ```
root@bt:~# sudo apt-get install crunch   Reading package lists... Done   Building dependency tree          Reading state information... Done   E: Couldn't find package crunch 
```   I have also had a problem just before this one occurred where I was trying to play a DVD so I installed VLC and had to uninstall it. I tried to re-install VLC through software centre and it wouldn't let me because the download contained unauthorized material.. This is know the same for any application in the software centre..    Could anybody help     Thanks for reading

---

### Post by abdullahDJ1 on 2011-07-11
[B]Hi, I just Installed Linux yesterday and I&#7743; having the same problem. :(
Open the Terminal and type in: Sudo [SIZE=2]apt-get install ms-ttcorefonts-installer
And if you get this error: [/SIZE][SIZE=2]Unable to locate package ms-ttcorefonts-installer.
Than you have to fix [/SIZE][SIZE=2]libula50 package manually. :(
And I don know how either. :(
[/SIZE][/B]

---

### Post by semt0x on 2011-07-11
I'll try that in a minute.. christ I don't even know how to format the orginal message properly 'code' etc lol

---

### Post by Bucky Ball on 2011-07-11
You can manually insert [code] tags or click 'Go Advanced' and select the bit you want in code tags and click the hash '#'. That does it automatically.

---

### Post by abdullahDJ1 on 2011-07-11
Bucky Ball waah? 
Can you explain that?
I&#7743; having the same problem .. :(

---

### Post by Bucky Ball on 2011-07-11
To do it manually you put the tag I showed in that last post first and this tag last: [/code].

I couldn't show you that in one post as everything between the code tags ...

 ```
 ... would look like this. 
```... if you get my drift. Use code tags as much easier for us to understand. ;)

 ```
 
```

---

### Post by abdullahDJ1 on 2011-07-11
oh, is this for putting the code inside this forum or fixing libula50 package manually?

---

### Post by Bucky Ball on 2011-07-11
What do you get when you run these two commands in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```? This will not upgrade the distro, only the packages you have installed, if they need upgrading. Also, is Crunch in the repos? i.e. is it in Synaptic package manager?

* Not that I can see.

* The easiest way to describe the code tags is that they are the same as [quote] tags. Mark the text you want inside the code tags, click the quote icon (speech bubble) and you will see the format. Change where it says 'quote' at the beginning and end tag to 'code' and you're done. ;)

* Is this what you are talking about? [http://www.bfsc.leidenuniv.nl/software/crunch/](http://www.bfsc.leidenuniv.nl/software/crunch/)

---

### Post by abdullahDJ1 on 2011-07-11
For sudo apt-get update ... I get:
```
Ign http://security.ubuntu.com natty-security InRelease
Ign http://ca.archive.ubuntu.com natty InRelease                    
Ign http://ca.archive.ubuntu.com natty-updates InRelease            
Get:1 http://packages.medibuntu.org natty InRelease [7,092 B]        
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://packages.medibuntu.org natty InRelease                         
Hit http://security.ubuntu.com natty-security Release.gpg                 
Hit http://ca.archive.ubuntu.com natty Release.gpg                             
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://security.ubuntu.com natty-security Release                          
Get:2 http://ca.archive.ubuntu.com natty-updates Release.gpg [198 B]           
Ign http://packages.medibuntu.org natty/free amd64 Packages/DiffIndex          
Hit http://extras.ubuntu.com natty Release                           
Hit http://ca.archive.ubuntu.com natty Release                                 
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://extras.ubuntu.com natty/main Sources                                
Get:3 http://ca.archive.ubuntu.com natty-updates Release [27.2 kB]             
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main amd64 Packages              
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages        
Ign http://packages.medibuntu.org natty/non-free amd64 Packages/DiffIndex      
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://security.ubuntu.com natty-security/universe amd64 Packages          
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages        
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Hit http://ca.archive.ubuntu.com natty/main Sources                            
Hit http://ca.archive.ubuntu.com natty/restricted Sources                      
Hit http://ca.archive.ubuntu.com natty/universe Sources                        
Hit http://ca.archive.ubuntu.com natty/multiverse Sources                      
Hit http://ca.archive.ubuntu.com natty/main amd64 Packages                     
Hit http://ca.archive.ubuntu.com natty/restricted amd64 Packages               
Hit http://ca.archive.ubuntu.com natty/universe amd64 Packages                 
Hit http://ca.archive.ubuntu.com natty/multiverse amd64 Packages               
Ign http://ca.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://ca.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://ca.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://ca.archive.ubuntu.com natty/universe TranslationIndex               
Get:4 http://ca.archive.ubuntu.com natty-updates/main Sources [92.1 kB]        
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Hit http://packages.medibuntu.org natty/free amd64 Packages                    
Get:5 http://ca.archive.ubuntu.com natty-updates/restricted Sources [14 B]     
Get:6 http://ca.archive.ubuntu.com natty-updates/universe Sources [17.9 kB]    
Get:7 http://ca.archive.ubuntu.com natty-updates/multiverse Sources [1,893 B]  
Get:8 http://ca.archive.ubuntu.com natty-updates/main amd64 Packages [268 kB]  
Hit http://packages.medibuntu.org natty/non-free amd64 Packages                
Get:9 http://ca.archive.ubuntu.com natty-updates/restricted amd64 Packages [14 B]
Get:10 http://ca.archive.ubuntu.com natty-updates/universe amd64 Packages [68.3 kB]
Ign http://extras.ubuntu.com natty/main Translation-en_CA                      
Get:11 http://ca.archive.ubuntu.com natty-updates/multiverse amd64 Packages [4,186 B]
Ign http://ca.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://ca.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://ca.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://ca.archive.ubuntu.com natty-updates/universe TranslationIndex       
Hit http://ca.archive.ubuntu.com natty/main Translation-en_CA                  
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://security.ubuntu.com natty-security/main Translation-en_CA           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Hit http://ca.archive.ubuntu.com natty/restricted Translation-en_CA            
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_CA     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_CA
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_CA
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://ca.archive.ubuntu.com natty/main Translation-en                     
Ign http://ca.archive.ubuntu.com natty/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com natty/multiverse Translation-en
Ign http://ca.archive.ubuntu.com natty/restricted Translation-en
Ign http://ca.archive.ubuntu.com natty/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com natty/universe Translation-en                 
Ign http://ca.archive.ubuntu.com natty-updates/main Translation-en_CA          
Ign http://ca.archive.ubuntu.com natty-updates/main Translation-en
Ign http://ca.archive.ubuntu.com natty-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://ca.archive.ubuntu.com natty-updates/restricted Translation-en_CA    
Ign http://ca.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://ca.archive.ubuntu.com natty-updates/universe Translation-en_CA      
Ign http://ca.archive.ubuntu.com natty-updates/universe Translation-en         
Ign http://packages.medibuntu.org natty/free Translation-en_CA
Ign http://packages.medibuntu.org natty/free Translation-en
Ign http://packages.medibuntu.org natty/non-free Translation-en_CA
Ign http://packages.medibuntu.org natty/non-free Translation-en
Fetched 480 kB in 6s (80.0 kB/s)                                               
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

And for sudo apt-get updrade I get: 
```
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                               &#9474; 
 &#9474; TrueType core fonts for the Web EULA                                            
 &#9474;                                                                                 
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                               
 &#9474;                                                                                 
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement ("EULA")    
 &#9474; is a legal agreement between you (either an individual or a single entity)      
 &#9474; and Microsoft Corporation for the Microsoft software accompanying this EULA,    
 &#9474; which includes computer software and may include associated media, printed      
 &#9474; materials, and "on-line" or electronic documentation ("SOFTWARE PRODUCT" or     
 &#9474; "SOFTWARE"). By exercising your rights to make and use copies of the            
 &#9474; SOFTWARE PRODUCT, you agree to be bound by the terms of this EULA. If you do    
 &#9474; not agree to the terms of this EULA, you may not use the SOFTWARE PRODUCT.      
 &#9474;                                                                                 
 &#9474; SOFTWARE PRODUCT LICENSE The SOFTWARE PRODUCT is protected by copyright laws    
 &#9474; and international copyright treaties, as well as other intellectual property    
 &#9474; laws and treaties. The SOFTWARE PRODUCT is licensed, not sold.                  
 &#9474;                                                                                 
 &#9474; 1. GRANT OF LICENSE. This EULA grants you the following rights:                 
 &#9474;                                                                                 
 &#9474;  • Installation and Use. You may install and use an unlimited number            
 &#9474;    of copies of the SOFTWARE PRODUCT.                                           
 &#9474;  • Reproduction and Distribution. You may reproduce and distribute              
 &#9474;                                                                                 
 &#9474;                                    <Ok>         
```
                                
 &#9474;                                                                               &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
And its stuck there, i cant click or anthing.. :(

---

### Post by semt0x on 2011-07-11
Ok the first one worked fine and the second one is in the process but this is on BT5 so i'll change to ubuntu when its finished to check there and I can see if its in the Synaptics Manager  Thank You    

* no its a word list generator

---

### Post by abdullahDJ1 on 2011-07-11
Ok I just Fixed the Problem. ŸeH

Here:
Try this what he said above:
```
sudo apt-get update sudo apt-get upgrade
```
Than for the second one:
You will get something like this:
[http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-for-ttf-mscorefonts-installer](http://askubuntu.com/questions/16225/how-can-i-accept-the-agreement-for-ttf-mscorefonts-installer)

Press Tab: And ÖK..
Than {Enter}
And it will automatically update everything than you can go back and try to download something from the terminal or Software Manager and it will work. ;)
Peace. If it works.

---

### Post by Bucky Ball on 2011-07-11
That is correct but make sure you do those commands separately, not in one line as shown above:

```
sudo apt-get update
```Then:

```

sudo apt-get upgrade
```Crunch is not in the repositories though so probably won't make any difference to that problem. Either need to figure out how to add the Crunch repo to your software sources or download and compile Crunch, one or the other. ;)

---

### Post by semt0x on 2011-07-12
Thank you I have also solved the problem with your help

---

### Post by Bucky Ball on 2011-07-12
Great. Could you please let us know how as it may help others. ;)

---

