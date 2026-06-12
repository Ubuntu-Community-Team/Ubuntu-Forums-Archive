---
title: "Update Manager Error"
date: 2012-07-06
forum: General Help
---

### Post by goodwine on 2012-07-06
Can anyone please help with a solution to the following error message I keep getting now when running update manager.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by Toz on 2012-07-06
Hello and welcome to the forums.

From a terminal prompt, try:
```

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```

This will delete the existing list files and re-create them again.

---

### Post by goodwine on 2012-07-07
Thanks very much Toz - went through the motions in Terminal - ran update manager again and got the same error message. Scrren dump from Terminal as below :

admin2@IBMPC:~$ sudo rm /vr/lib/apt/lists/* -vf
[sudo] password for admin2: 
admin2@IBMPC:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports InRelease        
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise InRelease                  
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security InRelease         
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates InRelease          
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports InRelease        
Ign [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed InRelease         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                 
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]            
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release.gpg [198 B]
Get:3 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise Release.gpg [198 B]      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release [39.8 kB]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                         
Get:5 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security Release.gpg [198 B]      
Get:6 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates Release.gpg [198 B]        
Get:7 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports Release.gpg [198 B]      
Get:8 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed Release.gpg [198 B]       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:9 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise Release [49.6 kB]                  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources/DiffIndex             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages/DiffIndex       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:10 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security Release [49.6 kB]        
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/main Sources [6,938 B]  
Get:12 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates Release [49.6 kB]         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources    
Get:13 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [4,982 B]
Get:14 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports Release [49.6 kB]       
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/restricted Sources [14 B]
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/universe Sources [10.8 kB]
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/multiverse Sources [14 B]
Get:18 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed Release [49.6 kB]        
Get:19 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/main Sources [934 kB]             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Get:20 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/restricted Sources [5,470 B]
Get:21 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/universe Sources [5,019 kB]
Get:22 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/multiverse Sources [155 kB]       
Get:23 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/main i386 Packages [1,274 kB]     
Get:24 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/restricted i386 Packages [8,431 B]
Get:25 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/universe i386 Packages [4,796 kB] 
Get:26 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/multiverse i386 Packages [121 kB] 
Get:27 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/main TranslationIndex [3,706 B]   
Get:28 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/multiverse TranslationIndex [2,676 B]
Get:29 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/restricted TranslationIndex [2,596 B]
Get:30 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/universe TranslationIndex [2,922 B]
Get:31 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/main Sources [22.5 kB]
Get:32 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/restricted Sources [14 B]
Get:33 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/universe Sources [7,832 B]
Get:34 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/multiverse Sources [713 B]
Get:35 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/main i386 Packages [70.2 kB]
Get:36 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/restricted i386 Packages [14 B]
Get:37 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/universe i386 Packages [19.0 kB]
Get:38 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/multiverse i386 Packages [1,394 B]
Get:39 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/main TranslationIndex [73 B]
Get:40 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/multiverse TranslationIndex [71 B]
Get:41 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/restricted TranslationIndex [70 B]
Get:42 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/universe TranslationIndex [73 B]
Get:43 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/restricted i386 Packages [2,439 B]
Get:44 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/main i386 Packages [314 kB]
Get:45 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/multiverse i386 Packages [2,047 B]
Get:46 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/universe i386 Packages [85.7 kB]
Get:47 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/main TranslationIndex [74 B]
Get:48 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/multiverse TranslationIndex [71 B]
Get:49 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/restricted TranslationIndex [71 B]
Get:50 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/universe TranslationIndex [73 B]
Get:51 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/restricted i386 Packages [14 B]
Get:52 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/main i386 Packages [1,271 B]
Get:53 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/multiverse i386 Packages [999 B]
Get:54 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/universe i386 Packages [9,703 B]
Get:55 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/main TranslationIndex [71 B]
Get:56 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/multiverse TranslationIndex [71 B]
Get:57 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/restricted TranslationIndex [70 B]
Get:58 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/universe TranslationIndex [72 B]
Get:59 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/restricted i386 Packages [14 B]
Get:60 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/main i386 Packages [166 kB]
Get:61 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/multiverse i386 Packages [14 B]
Get:62 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/universe i386 Packages [22.5 kB]
Get:63 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/main TranslationIndex [3,564 B]
Get:64 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/multiverse TranslationIndex [2,605 B]
Get:65 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/restricted TranslationIndex [2,461 B]
Get:66 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/universe TranslationIndex [2,850 B]
Get:67 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/main Translation-en [726 kB]      
Get:68 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/multiverse Translation-en [93.4 kB]
Get:69 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/restricted Translation-en [2,395 B]
Get:70 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise/universe Translation-en [3,341 kB]
Get:71 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/main Translation-en [35.5 kB]
Get:72 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/multiverse Translation-en [587 B]
Get:73 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/restricted Translation-en [14 B]
Get:74 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-security/universe Translation-en [12.8 kB]
Get:75 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/main Translation-en [145 kB]
Get:76 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/multiverse Translation-en [912 B]
Get:77 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/restricted Translation-en [798 B]
Get:78 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-updates/universe Translation-en [51.1 kB]
Get:79 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/main Translation-en [908 B]
Get:80 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/multiverse Translation-en [422 B]
Get:81 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/restricted Translation-en [14 B]
Get:82 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-backports/universe Translation-en [7,073 B]
Get:83 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/main Translation-en [53.2 kB]
Get:84 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/multiverse Translation-en [14 B]
Get:85 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/restricted Translation-en [14 B]
Get:86 [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) precise-proposed/universe Translation-en [13.9 kB]
Fetched 17.9 MB in 1min 9s (256 kB/s)                                          
Reading package lists... Error!
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
admin2@IBMPC:~$

---

### Post by Bigtime_Scrub on 2012-07-07
That problem can happen if you have too many sources in your repos. Double check them to make sure you don't have typos in there and also make sure there are no double posts of it. If you have a lot of ppas and sources from all over the place I would recommend you cut them down a bit. 

Try this again one more time:

```
sudo rm /var/lib/apt/lists/* -vf
```
```
sudo apt-get clean
```
```
sudo apt-get update
```

Do the commands one at a time. If that does not work...
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists-old
```
```
sudo mkdir -p /var/lib/apt/lists/partial
```
```
sudo apt-get update
```

---

### Post by goodwine on 2012-07-07
Many thanks indeed - the second option worked and Update Manager now working as normal again. Once again many thanks. Greg (Bristol UK)

---

### Post by Old Norm on 2012-07-19
> **Toz said:**
> Hello and welcome to the forums.

From a terminal prompt, try:
```

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```This will delete the existing list files and re-create them again.

This Has Solved My Problem Many Thanks
Regards Old Norm

---

### Post by Old Norm on 2012-07-19
This Has Solved My Problem Many Thanks
Regards Old Norm
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=12114703") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=12114703")

---

