---
title: "Lucid Netbook - some repos. fail, updates install, date does not refresh anymore"
date: 2012-01-14
forum: General Help
---

### Post by Pi-Rat on 2012-01-14
I frequently check for updates and still have automatic updates show up (most of the time). These will hit the repositories, where at least one will fail. Then the updates from the other repositories download and install fine. The date I last updated my system no longer refreshes to "Your system last updated 1 day ago," and is now stuck on 44 days ago: even though updates have come several times during those 44 days. I have also been getting automatic update failures starting since that day 44 days ago, but not often. Running "sudo apt-get update" and "sudo apt-get upgrade" from command line don't remedy this either. At a loss as to what to do to correct this and not able to find a bug report on this or if I should even file a bug report. Any ideas on what to do next? ](*,)

[IMG]http://i128.photobucket.com/albums/p196/Pi-Rat/updateerrorsmall.png[/IMG]

[IMG]http://i128.photobucket.com/albums/p196/Pi-Rat/errorrepositoryupdates.png[/IMG]

[IMG]http://i128.photobucket.com/albums/p196/Pi-Rat/updatemanagerupdatingbutnoresettodate.png[/IMG]

```
susan@BUNTop:~$ sudo apt-get upgrade
[sudo] password for susan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
susan@BUNTop:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-security Release.gpg                
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                             
Hit http://us.archive.ubuntu.com lucid-updates Release                     
Hit http://us.archive.ubuntu.com lucid-security Release                        
Hit http://us.archive.ubuntu.com lucid/main Sources                            
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://us.archive.ubuntu.com lucid/main Packages                       
Hit http://us.archive.ubuntu.com lucid/restricted Packages                 
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                  
Hit http://us.archive.ubuntu.com lucid/universe Sources                        
Hit http://us.archive.ubuntu.com lucid/universe Packages                       
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                 
Hit http://us.archive.ubuntu.com lucid-updates/main Packages               
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages         
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources              
Hit http://us.archive.ubuntu.com lucid-updates/main Sources                    
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources                
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages               
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages         
Hit http://us.archive.ubuntu.com lucid-security/main Packages              
Hit http://us.archive.ubuntu.com lucid-security/restricted Packages        
Hit http://us.archive.ubuntu.com lucid-security/restricted Sources             
Hit http://us.archive.ubuntu.com lucid-security/main Sources                   
Hit http://us.archive.ubuntu.com lucid-security/multiverse Sources         
Hit http://us.archive.ubuntu.com lucid-security/universe Sources           
Hit http://us.archive.ubuntu.com lucid-security/universe Packages          
Hit http://us.archive.ubuntu.com lucid-security/multiverse Packages        
Get:1 http://archive.canonical.com lucid Release.gpg [198B]                
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US   
Hit http://archive.canonical.com lucid Release
Hit http://archive.canonical.com lucid/partner Packages    
Hit http://archive.canonical.com lucid/partner Sources
Err http://ppa.launchpad.net lucid Release.gpg                                 
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid/main Packages                               
Fetched 198B in 10s (19B/s)                                                    
W: Failed to fetch http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by Old_Grey_Wolf on 2012-01-14
Looks like a problem with the mozilla PPA. Open "Software Sources" go to the "Other Software" tab and remove the check next to the mozilla PPA. If you can update after that then add the moziall PPA back to you sources with this command ```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```.

---

### Post by Pi-Rat on 2012-01-14
Thanks, Old_Gray_Wolf.
Well, that got the date of last updated to reset to the "lass than an hour ago" message. The "http://archive.canonical.com/ubuntu/dists/lucid/Release.gpg" still didn't resolve, but everything else seems ok. Then re-added the firefox PPA. Tried it graphically with Update Manager and command line, same thing happened. 

'Course leaves me to wonder if it'll do that again in a few days. Going to be wondering for months now how/why that worked without the firefox PPA. Does Ubuntu just not like me and is suggesting this way I should see other distros?

---

### Post by Old_Grey_Wolf on 2012-01-14
Let's try to resolve the other errors.

Enter this command and post the output ```
sudo apt-get update
``` Then enter this command and post the output ```
sudo apt-get upgrade
```

Edit: DOH, I was reading your forum name as &#960;-Rat, funny. ;-)

> **Pi-Rat said:**
> Does Ubuntu just not like me and is suggesting this way I should see other distros?
The repo problem you are having is not unique to Ubuntu.

---

### Post by Pi-Rat on 2012-01-14
> **Old_Gray_Wolf said:**
> 

Edit: DOH, I was reading your forum name as &#960;-Rat, funny. ;-)


The repo problem you are having is not unique to Ubuntu.

Thanks. Used to have an avatar of a &#960; then an ASCII drawn rat face, but seem to have misplaced my files.
Was also just trying to sound like a humorous, but inept and jealous lover with that comment. Heh.

Ran both commands and firefox did the no host again, so performed the disable and re-add of the repo. Then ran the commands again. Here's the output:
```
susan@BUNTop:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-security Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release         
Hit http://us.archive.ubuntu.com lucid-security Release                              
Hit http://us.archive.ubuntu.com lucid/main Sources                                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources      
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid-security/restricted Packages
Hit http://us.archive.ubuntu.com lucid-security/restricted Sources
Hit http://us.archive.ubuntu.com lucid-security/main Sources   
Hit http://us.archive.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-security/universe Sources
Hit http://us.archive.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://archive.canonical.com lucid Release
Hit http://archive.canonical.com lucid/partner Packages
Hit http://archive.canonical.com lucid/partner Sources
Reading package lists... Done
susan@BUNTop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Seems to be an intermittent failure and behaving in front of witnesses. I wondered months ago if it was just a WiFi flaky connection, so I shut of wireless and went hard-wired for 2 weeks and did the same thing.

---

### Post by Old_Grey_Wolf on 2012-01-14
It may be an intermittent problem with the repo mirror server you are using. If you haven't already tried this, you could try switching mirror servers. Open "Update Manager", click the "Settings..." button, then select "Other..." from the "Download from menu", then click the "Select Best Server" button, let it run its tests, then click the "Choose Server" button. It will then ask you to reload.

> **Pi-Rat said:**
> Used to have an avatar of a &#960; then an ASCII drawn rat face, but seem to have misplaced my files.


Something like these? ```
<^__)~

or

~(__^> 

or

 .     ,
 (\,;,/)
  (0 0)\__,
   \ /     \,
   `o'(  (   \    )
      //  \   |_./
    '~'  '--__'    


```
> **Pi-Rat said:**
> 
Was also just trying to sound like a humorous, but inept and jealous lover with that comment. Heh.

I'm 63 years old; therefore, I never would have figured that out. LOL

Please mark the thread as solved if you no long have problems. If you do not know how to do that, near the top of the webpage (scroll up) there is a menu "Thread Tools". Select "Mark this thread as solved". It lets other people searching the forums know that this had a working solution and they don't need to provide additional help.

Thank you.

---

### Post by Pi-Rat on 2012-01-14
Looks like the best server option wins. Now a Texas University mirror is loading them. Didn't even notice that button before. I had tried manually switching the servers before (at random). Thanks again.

P.S. I am also jealous of your ASCII skillz. Found my avatar finally. Once I'm established enough on the boards I'll upload it. Here's what it looks like:
[IMG]http://i128.photobucket.com/albums/p196/Pi-Rat/pi-av-big.jpg[/IMG]

---

