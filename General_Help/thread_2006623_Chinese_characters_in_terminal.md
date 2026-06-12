---
title: "Chinese characters in terminal"
date: 2012-06-19
forum: General Help
---

### Post by blakegrover on 2012-06-19
After being away from Ubuntu for a year I have came back and I have really liked the improvements in the latest release.  The only issue I have found is that in the terminal some programs display Chinese characters where it should be English.  I have checked my language settings and everything looks ok in there.  In fact in the area where you choose what languages to install (Chinese isn't even selected).  Below is a sample of running aptitude update, aptitude upgrade, and a df -h command.

```
root@groverb:~# aptitude update
Ign http://moros.byui.edu precise InRelease
Ign http://moros.byui.edu precise-updates InRelease                                                          
Ign http://moros.byui.edu precise-backports InRelease                                                        
Get: 1 http://moros.byui.edu precise Release.gpg [198 B]                                                     
Get: 2 http://moros.byui.edu precise-updates Release.gpg [198 B]                                             
Get: 3 http://moros.byui.edu precise-backports Release.gpg [198 B]                                           
Get: 4 http://moros.byui.edu precise Release [49.6 kB]                                                       
Get: 5 http://moros.byui.edu precise-updates Release [49.6 kB]                                               
Get: 6 http://moros.byui.edu precise-backports Release [49.6 kB]                                             
Hit http://moros.byui.edu precise/main Sources                                                               
Hit http://moros.byui.edu precise/restricted Sources                                                         
Hit http://moros.byui.edu precise/universe Sources                                                           
Hit http://moros.byui.edu precise/multiverse Sources                                                         
Hit http://moros.byui.edu precise/main i386 Packages
Hit http://moros.byui.edu precise/restricted i386 Packages                                                   
Hit http://moros.byui.edu precise/universe i386 Packages
Hit http://moros.byui.edu precise/multiverse i386 Packages                                                   
Ign http://moros.byui.edu precise/main TranslationIndex                                                      
Ign http://moros.byui.edu precise/multiverse TranslationIndex                                                
Ign http://moros.byui.edu precise/restricted TranslationIndex
Ign http://moros.byui.edu precise/universe TranslationIndex                                                  
Ign http://dl.google.com stable InRelease                                                                    
Get: 7 http://moros.byui.edu precise-updates/main Sources [112 kB]                                           
Hit http://moros.byui.edu precise-updates/restricted Sources                                                 
Get: 8 http://moros.byui.edu precise-updates/universe Sources [25.4 kB]
Hit http://moros.byui.edu precise-updates/multiverse Sources
Get: 9 http://dl.google.com stable Release.gpg [198 B]                                                       
Ign http://linux.dropbox.com precise InRelease                                                               
Get: 10 http://moros.byui.edu precise-updates/main i386 Packages [288 kB]                                    
Hit http://moros.byui.edu precise-updates/restricted i386 Packages                                           
Get: 11 http://moros.byui.edu precise-updates/universe i386 Packages [73.2 kB]                               
Get: 12 http://dl.google.com stable Release [1,347 B]                                                        
Hit http://moros.byui.edu precise-updates/multiverse i386 Packages                                           
Ign http://moros.byui.edu precise-updates/main TranslationIndex                                              
Ign http://moros.byui.edu precise-updates/multiverse TranslationIndex
Ign http://moros.byui.edu precise-updates/restricted TranslationIndex
Ign http://moros.byui.edu precise-updates/universe TranslationIndex
Hit http://moros.byui.edu precise-backports/main Sources                                                     
Hit http://moros.byui.edu precise-backports/restricted Sources
Hit http://moros.byui.edu precise-backports/universe Sources                                                 
Hit http://moros.byui.edu precise-backports/multiverse Sources
Hit http://moros.byui.edu precise-backports/main i386 Packages
Hit http://moros.byui.edu precise-backports/restricted i386 Packages
Hit http://moros.byui.edu precise-backports/universe i386 Packages
Hit http://moros.byui.edu precise-backports/multiverse i386 Packages                                         
Ign http://moros.byui.edu precise-backports/main TranslationIndex                                            
Ign http://moros.byui.edu precise-backports/multiverse TranslationIndex                                      
Ign http://moros.byui.edu precise-backports/restricted TranslationIndex                                      
Ign http://moros.byui.edu precise-backports/universe TranslationIndex                                        
Hit http://linux.dropbox.com precise Release.gpg                                                             
Ign http://moros.byui.edu precise/main Translation-zh_CN                                                    
Ign http://moros.byui.edu precise/main Translation-zh                                                       
Ign http://moros.byui.edu precise/main Translation-en                                                       
Ign http://moros.byui.edu precise/multiverse Translation-zh_CN
Ign http://moros.byui.edu precise/multiverse Translation-zh                                                  
Ign http://moros.byui.edu precise/multiverse Translation-en
Ign http://moros.byui.edu precise/restricted Translation-zh_CN
Ign http://moros.byui.edu precise/restricted Translation-zh
Ign http://moros.byui.edu precise/restricted Translation-en                                                 
Ign http://moros.byui.edu precise/universe Translation-zh_CN
Ign http://moros.byui.edu precise/universe Translation-zh                                                    
Ign http://moros.byui.edu precise/universe Translation-en                                                    
Ign http://moros.byui.edu precise-updates/main Translation-zh_CN                                            
Ign http://moros.byui.edu precise-updates/main Translation-zh                                               
Ign http://moros.byui.edu precise-updates/main Translation-en                                               
Ign http://moros.byui.edu precise-updates/multiverse Translation-zh_CN                                       
Ign http://moros.byui.edu precise-updates/multiverse Translation-zh
Ign http://moros.byui.edu precise-updates/multiverse Translation-en                                         
Ign http://moros.byui.edu precise-updates/restricted Translation-zh_CN
Ign http://moros.byui.edu precise-updates/restricted Translation-zh                                          
Ign http://moros.byui.edu precise-updates/restricted Translation-en                                          
Ign http://moros.byui.edu precise-updates/universe Translation-zh_CN                                        
Ign http://moros.byui.edu precise-updates/universe Translation-zh                                            
Ign http://moros.byui.edu precise-updates/universe Translation-en
Ign http://moros.byui.edu precise-backports/main Translation-zh_CN                                          
Ign http://moros.byui.edu precise-backports/main Translation-zh
Ign http://moros.byui.edu precise-backports/main Translation-en                                             
Ign http://moros.byui.edu precise-backports/multiverse Translation-zh_CN                                    
Ign http://moros.byui.edu precise-backports/multiverse Translation-zh                                       
Ign http://moros.byui.edu precise-backports/multiverse Translation-en
Ign http://moros.byui.edu precise-backports/restricted Translation-zh_CN                                    
Ign http://moros.byui.edu precise-backports/restricted Translation-zh                                        
Ign http://moros.byui.edu precise-backports/restricted Translation-en
Ign http://moros.byui.edu precise-backports/universe Translation-zh_CN                                      
Ign http://moros.byui.edu precise-backports/universe Translation-zh                                          
Ign http://moros.byui.edu precise-backports/universe Translation-en                                          
Get: 13 http://dl.google.com stable/main i386 Packages [1,249 B]                                             
Hit http://linux.dropbox.com precise Release                                                                 
Ign http://security.ubuntu.com precise-security InRelease                                                    
Ign http://ppa.launchpad.net precise InRelease                                                               
Ign http://ppa.launchpad.net precise InRelease                                                               
Ign http://ppa.launchpad.net precise InRelease
Ign http://archive.canonical.com precise InRelease                                                           
Hit http://linux.dropbox.com precise/main i386 Packages                                                      
Ign http://dl.google.com stable/main TranslationIndex                                                        
Ign http://extras.ubuntu.com precise InRelease                                                               
Hit http://deb.playonlinux.com precise InRelease                                              
Ign http://linux.dropbox.com precise/main TranslationIndex                                    
Get: 14 http://security.ubuntu.com precise-security Release.gpg [198 B]                       
Hit http://ppa.launchpad.net precise Release.gpg                                                            
Hit http://ppa.launchpad.net precise Release.gpg                                                             
Hit http://archive.canonical.com precise Release.gpg                                          
Get: 15 http://extras.ubuntu.com precise Release.gpg [72 B]                                   
Hit http://deb.playonlinux.com precise/main i386 Packages                                     
Get: 16 http://security.ubuntu.com precise-security Release [49.6 kB]                         
Get: 17 http://ppa.launchpad.net precise Release.gpg [316 B]                                                 
Hit http://ppa.launchpad.net precise Release                                                                 
Hit http://archive.canonical.com precise Release                                                             
Hit http://extras.ubuntu.com precise Release                                                                 
Hit http://ppa.launchpad.net precise Release                                                                 
Get: 18 http://ppa.launchpad.net precise Release [11.9 kB]                                                  
Hit http://archive.canonical.com precise/partner i386 Packages                                               
Hit http://ppa.launchpad.net precise/main Sources                                                            
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://linux.dropbox.com precise/main Translation-zh_CN                                                 
Hit http://extras.ubuntu.com precise/main Sources                                                            
Ign http://archive.canonical.com precise/partner TranslationIndex                                           
Ign http://linux.dropbox.com precise/main Translation-zh                                                    
Ign http://linux.dropbox.com precise/main Translation-en                                                    
Hit http://ppa.launchpad.net precise/main Sources                                                           
Hit http://extras.ubuntu.com precise/main i386 Packages                                                     
Ign http://extras.ubuntu.com precise/main TranslationIndex                                      
Hit http://ppa.launchpad.net precise/main i386 Packages                                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                  
Ign http://deb.playonlinux.com precise/main TranslationIndex                                    
Get: 19 http://ppa.launchpad.net precise/main Sources [2,228 B]                                 
Get: 20 http://security.ubuntu.com precise-security/main Sources [20.1 kB]                        
Get: 21 http://ppa.launchpad.net precise/main i386 Packages [3,824 B]                                       
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                  
Get: 22 http://security.ubuntu.com precise-security/restricted Sources [14 B]                 
Get: 23 http://security.ubuntu.com precise-security/universe Sources [6,150 B]              
Get: 24 http://security.ubuntu.com precise-security/multiverse Sources [713 B]                    
Get: 25 http://security.ubuntu.com precise-security/main i386 Packages [64.6 kB]              
Ign http://dl.google.com stable/main Translation-zh_CN                                                      
Ign http://dl.google.com stable/main Translation-zh                              
Ign http://dl.google.com stable/main Translation-en                               
Get: 26 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get: 27 http://security.ubuntu.com precise-security/universe i386 Packages [14.9 kB]
Ign http://extras.ubuntu.com precise/main Translation-zh_CN                       
Get: 28 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B] 
Get: 29 http://security.ubuntu.com precise-security/main TranslationIndex [73 B]
Get: 30 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get: 31 http://security.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get: 32 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]                      
Get: 33 http://security.ubuntu.com precise-security/main Translation-en [32.2 kB]
Ign http://extras.ubuntu.com precise/main Translation-zh                                
Ign http://extras.ubuntu.com precise/main Translation-en                 
Ign http://archive.canonical.com precise/partner Translation-zh_CN       
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Ign http://archive.canonical.com precise/partner Translation-zh
Get: 34 http://security.ubuntu.com precise-security/universe Translation-en [10.1 kB]
Ign http://archive.canonical.com precise/partner Translation-en            
Ign http://ppa.launchpad.net precise/main Translation-zh_CN
Ign http://ppa.launchpad.net precise/main Translation-zh
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-zh_CN
Ign http://ppa.launchpad.net precise/main Translation-zh
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-zh_CN
Ign http://ppa.launchpad.net precise/main Translation-zh
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://deb.playonlinux.com precise/main Translation-zh_CN
Ign http://deb.playonlinux.com precise/main Translation-zh
Ign http://deb.playonlinux.com precise/main Translation-en
Fetched 869 kB in 5&#31186; (167 kB/s)
                         
Current status: 10 updates [+10].
root@groverb:~# aptitude upgrade
The following packages will be upgraded: 
  gnome-settings-daemon libpam-smbpass libpam-winbind libsmbclient libwbclient0 samba samba-common 
  samba-common-bin smbclient winbind 
10 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.9 MB of archives. After unpacking 0 B will be used.
Do you want to continue? [Y/n/?] y
Get: 1 http://moros.byui.edu/ubuntu/ precise-updates/main libpam-winbind i386 2:3.6.3-2ubuntu2.3 [624 kB]
Get: 2 http://moros.byui.edu/ubuntu/ precise-updates/main winbind i386 2:3.6.3-2ubuntu2.3 [4,399 kB]
Get: 3 http://moros.byui.edu/ubuntu/ precise-updates/main samba i386 2:3.6.3-2ubuntu2.3 [8,010 kB]
Get: 4 http://moros.byui.edu/ubuntu/ precise-updates/main libwbclient0 i386 2:3.6.3-2ubuntu2.3 [30.8 kB]
Get: 5 http://moros.byui.edu/ubuntu/ precise-updates/main smbclient i386 2:3.6.3-2ubuntu2.3 [14.0 MB]
Get: 6 http://moros.byui.edu/ubuntu/ precise-updates/main libpam-smbpass i386 2:3.6.3-2ubuntu2.3 [762 kB]
Get: 7 http://moros.byui.edu/ubuntu/ precise-updates/main samba-common-bin i386 2:3.6.3-2ubuntu2.3 [6,153 kB]
Get: 8 http://moros.byui.edu/ubuntu/ precise-updates/main samba-common all 2:3.6.3-2ubuntu2.3 [325 kB]
Get: 9 http://moros.byui.edu/ubuntu/ precise-updates/main libsmbclient i386 2:3.6.3-2ubuntu2.3 [2,135 kB]
Get: 10 http://moros.byui.edu/ubuntu/ precise-updates/main gnome-settings-daemon i386 3.4.2-0ubuntu0.1 [479 kB]
Fetched 36.9 MB in 1&#31186; (23.2 MB/s)              
&#27491;&#22312;&#39044;&#35774;&#23450;&#36719;&#20214;&#21253; ...
(&#27491;&#22312;&#35835;&#21462;&#25968;&#25454;&#24211; ... &#31995;&#32479;&#24403;&#21069;&#20849;&#23433;&#35013;&#26377; 220678 &#20010;&#25991;&#20214;&#21644;&#30446;&#24405;&#12290;)
&#27491;&#39044;&#22791;&#26367;&#25442; libpam-winbind 2:3.6.3-2ubuntu2.2 (&#20351;&#29992; .../libpam-winbind_2%3a3.6.3-2ubuntu2.3_i386.deb) ...
&#27491;&#22312;&#35299;&#21387;&#32553;&#23558;&#29992;&#20110;&#26356;&#26367;&#30340;&#21253;&#25991;&#20214; libpam-winbind ...
&#27491;&#39044;&#22791;&#26367;&#25442; winbind 2:3.6.3-2ubuntu2.2 (&#20351;&#29992; .../winbind_2%3a3.6.3-2ubuntu2.3_i386.deb) ...
 * Stopping the Winbind daemon winbind                                                                [ OK ] 
&#27491;&#22312;&#35299;&#21387;&#32553;&#23558;&#29992;&#20110;&#26356;&#26367;&#30340;&#21253;&#25991;&#20214; winbind ...
&#27491;&#39044;&#22791;&#26367;&#25442; samba 2:3.6.3-2ubuntu2.2 (&#20351;&#29992; .../samba_2%3a3.6.3-2ubuntu2.3_i386.deb) ...
nmbd stop/waiting
smbd stop/waiting
&#27491;&#22312;&#35299;&#21387;&#32553;&#23558;&#29992;&#20110;&#26356;&#26367;&#30340;&#21253;&#25991;&#20214; samba ...
&#27491;&#39044;&#22791;&#26367;&#25442; libwbclient0 2:3.6.3-2ubuntu2.2 (&#20351;&#29992; .../libwbclient0_2%3a3.6.3-2ubuntu2.3_i386.deb) ...
&#27491;&#22312;&#35299;&#21387;&#32553;&#23558;&#29992;&#20110;&#26356;&#26367;&#30340;&#21253;&#25991;&#20214; libwbclient0 ...
&#27491;&#39044;&#22791;&#26367;&#25442; smbclient 2:3.6.3-2ubuntu2.2 (&#20351;&#29992; .../smbclient_2%3a3.6.3-2ubuntu2.3_i386.deb) ...
&#27491;&#22312;&#35299;&#21387;&#32553;&#23558;&#29992;&#20110;&#26356;&#26367;&#30340;&#21253;&#25991;&#20214; smbclient ...
&#27491;&#39044;&#22791;&#26367;&#25442; libpam-smbpass 2:3.6.3-2ubuntu2.2 (&#20351;&#29992; .../libpam-smbpass_2%3a3.6.3-2ubuntu2.3_i386.deb) ...
&#27491;&#22312;&#35299;&#21387;&#32553;&#23558;&#29992;&#20110;&#26356;&#26367;&#30340;&#21253;&#25991;&#20214; libpam-smbpass ...
&#27491;&#39044;&#22791;&#26367;&#25442; samba-common-bin 2:3.6.3-2ubuntu2.2 (&#20351;&#29992; .../samba-common-bin_2%3a3.6.3-2ubuntu2.3_i386.deb) ...
&#27491;&#22312;&#35299;&#21387;&#32553;&#23558;&#29992;&#20110;&#26356;&#26367;&#30340;&#21253;&#25991;&#20214; samba-common-bin ...
&#27491;&#39044;&#22791;&#26367;&#25442; samba-common 2:3.6.3-2ubuntu2.2 (&#20351;&#29992; .../samba-common_2%3a3.6.3-2ubuntu2.3_all.deb) ...
&#27491;&#22312;&#35299;&#21387;&#32553;&#23558;&#29992;&#20110;&#26356;&#26367;&#30340;&#21253;&#25991;&#20214; samba-common ...
&#27491;&#39044;&#22791;&#26367;&#25442; libsmbclient 2:3.6.3-2ubuntu2.2 (&#20351;&#29992; .../libsmbclient_2%3a3.6.3-2ubuntu2.3_i386.deb) ...
&#27491;&#22312;&#35299;&#21387;&#32553;&#23558;&#29992;&#20110;&#26356;&#26367;&#30340;&#21253;&#25991;&#20214; libsmbclient ...
&#27491;&#39044;&#22791;&#26367;&#25442; gnome-settings-daemon 3.4.1-0ubuntu1.1 (&#20351;&#29992; .../gnome-settings-daemon_3.4.2-0ubuntu0.1_i386.deb) ...
&#27491;&#22312;&#35299;&#21387;&#32553;&#23558;&#29992;&#20110;&#26356;&#26367;&#30340;&#21253;&#25991;&#20214; gnome-settings-daemon ...
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; man-db &#30340;&#35302;&#21457;&#22120;...
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; ureadahead &#30340;&#35302;&#21457;&#22120;...
ureadahead will be reprofiled on next reboot
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; ufw &#30340;&#35302;&#21457;&#22120;...
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; libglib2.0-0 &#30340;&#35302;&#21457;&#22120;...
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; gconf2 &#30340;&#35302;&#21457;&#22120;...
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; hicolor-icon-theme &#30340;&#35302;&#21457;&#22120;...
&#27491;&#22312;&#35774;&#32622; libwbclient0 (2:3.6.3-2ubuntu2.3) ...
&#27491;&#22312;&#35774;&#32622; samba-common (2:3.6.3-2ubuntu2.3) ...
&#27491;&#22312;&#35774;&#32622; winbind (2:3.6.3-2ubuntu2.3) ...
 * Starting the Winbind daemon winbind                                                                [ OK ] 
&#27491;&#22312;&#35774;&#32622; libpam-winbind (2:3.6.3-2ubuntu2.3) ...
&#27491;&#22312;&#35774;&#32622; samba-common-bin (2:3.6.3-2ubuntu2.3) ...
&#27491;&#22312;&#35774;&#32622; samba (2:3.6.3-2ubuntu2.3) ...
&#27491;&#22312;&#23433;&#35013;&#26032;&#29256;&#26412;&#30340;&#37197;&#32622;&#25991;&#20214; /etc/init/nmbd.conf ...
smbd start/running, process 14503
nmbd start/running, process 14537
&#27491;&#22312;&#35774;&#32622; smbclient (2:3.6.3-2ubuntu2.3) ...
&#27491;&#22312;&#35774;&#32622; libpam-smbpass (2:3.6.3-2ubuntu2.3) ...
&#27491;&#22312;&#35774;&#32622; libsmbclient (2:3.6.3-2ubuntu2.3) ...
&#27491;&#22312;&#35774;&#32622; gnome-settings-daemon (3.4.2-0ubuntu0.1) ...
&#27491;&#22312;&#22788;&#29702;&#29992;&#20110; libc-bin &#30340;&#35302;&#21457;&#22120;...
ldconfig deferred processing now taking place
                                         
Current status: 0 updates [-10].
root@groverb:~# aptitude clean
root@groverb:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        11G  9.7G  583M  95% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           788M  1.2M  787M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  1.2M  2.0G   1% /run/shm
/dev/sda2       146G   49G   98G  34% /media/Data

```

For those who think it is because I am using aptitude and not apt-get, I get the same Chinese characters in the apt-get commands.  I assume it is Chinese since when I translate the phrases in Google Translate it marks it as Chinese.  

I able to continue working in Ubuntu but it will slowly become an annoyance if I can't get it fixed

---

### Post by drmrgd on 2012-06-19
Your list of sources looks a bit weird.  Why are you pulling your packages from the moros.byui.edu mirror rather than the official repos? 

Also, it looks like you're also pulling from the Chinese versions of those repos as well.  I would recommend removing the Chinese translations from your sources list and trying again.  I'll bet that has something to do with what you're seeing.

---

### Post by blakegrover on 2012-06-19
> **drmrgd said:**
> Your list of sources looks a bit weird.  Why are you pulling your packages from the moros.byui.edu mirror rather than the official repos? 

Also, it looks like you're also pulling from the Chinese versions of those repos as well.  I would recommend removing the Chinese translations from your sources list and trying again.  I'll bet that has something to do with what you're seeing.

I use our local source since the downloads are super fast (1GB internal network instead of having to outside our network).  I can switch it back though to test.  

Here is my sources.list file.  I don't see any Chinese sources being used

```
root@groverb:~# more /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
# us.archive.ubuntu.com

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://moros.byui.edu/ubuntu/ precise main restricted
deb-src http://moros.byui.edu/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://moros.byui.edu/ubuntu/ precise-updates main restricted
deb-src http://moros.byui.edu/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://moros.byui.edu/ubuntu/ precise universe
deb-src http://moros.byui.edu/ubuntu/ precise universe
deb http://moros.byui.edu/ubuntu/ precise-updates universe
deb-src http://moros.byui.edu/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://moros.byui.edu/ubuntu/ precise multiverse
deb-src http://moros.byui.edu/ubuntu/ precise multiverse
deb http://moros.byui.edu/ubuntu/ precise-updates multiverse
deb-src http://moros.byui.edu/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://moros.byui.edu/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://moros.byui.edu/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

---

### Post by flmommens on 2012-11-03
I was also affected by this issue. I solved it by copying the .pam_environment file from my home directory to root's home directory. That file was missing for some reason.
My .pam_environment file contains:
LANGUAGE=en
LANG=en_US.UTF-8
LC_NUMERIC=en_US.UTF-8
LC_TIME=en_US.UTF-8
LC_MONETARY=en_US.UTF-8
LC_PAPER=en_US.UTF-8
LC_NAME=en_US.UTF-8
LC_ADDRESS=en_US.UTF-8
LC_TELEPHONE=en_US.UTF-8
LC_MEASUREMENT=en_US.UTF-8
LC_IDENTIFICATION=en_US.UTF-8

---

