---
title: "cannot get updates &quot;cannot find repository&quot;error"
date: 2009-08-30
forum: General Help
---

### Post by hairchin67 on 2009-08-30
when trying to get updates this is what i get

how do i fix this?

---

### Post by NoaHall on 2009-08-30
sudo apt-get update and post the results here.

---

### Post by hairchin67 on 2009-08-30
> **NoaHall said:**
> sudo apt-get update and post the results here.

how do i post the results from the terminal?

---

### Post by NoaHall on 2009-08-30
Copy and paste....... select the output with a mouse, and then using "ctrl + shift + c" and then paste them onto here

---

### Post by hairchin67 on 2009-08-30
> **NoaHall said:**
> Copy and paste....... select the output with a mouse, and then using "ctrl + shift + c" and then paste them onto here

im a rookie please bear with me but the terminal wont let me copy it only will let me paste the copy is not hi lited and ive never used ctrl shift +c im used to right click copy and paste please explain more precisely thanxcraig@craig-desktop:~$ sudo apt-get update
Err http: //ppa. Release.gpg
  Unable to connect to  http:
Err http: //ppa./launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu Translation-en_US
  Unable to connect to  http:
Err http: //ppa./jaunty Translation-en_US
  Unable to connect to  http:
Err http: //ppa./main Translation-en_US
  Unable to connect to  http:
Ign http: //ppa. Release                                                       
Ign http: //ppa./launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu Packages        
Ign http: //ppa./jaunty Packages                                               
Ign http: //ppa./main Packages                                                 
Err http: //ppa./launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu Packages        
  Unable to connect to  http:
Err http: //ppa./jaunty Packages                                               
  Unable to connect to  http:
Err http: //ppa./main Packages                                                 
  Unable to connect to  http:
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
W: Failed to fetch http:/dists///ppa./Release.gpg  Unable to connect to  http:

W: Failed to fetch http:/dists///ppa./launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/i18n/Translation-en_US.bz2  Unable to connect to  http:

W: Failed to fetch http:/dists///ppa./jaunty/i18n/Translation-en_US.bz2  Unable to connect to  http:

W: Failed to fetch http:/dists///ppa./main/i18n/Translation-en_US.bz2  Unable to connect to  http:

W: Failed to fetch http:/dists///ppa./launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/binary-i386/Packages.gz  Unable to connect to  http:

W: Failed to fetch http:/dists///ppa./jaunty/binary-i386/Packages.gz  Unable to connect to  http:

W: Failed to fetch http:/dists///ppa./main/binary-i386/Packages.gz  Unable to connect to  http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
craig@craig-desktop:~$ sudo apt-get updatesudo apt-get updatesudo apt-get update

---

### Post by NoaHall on 2009-08-30
That shows that some of the sources haven't been entered correctly - there should be no space between the "http:" and the "//". Use from the terminal "gksudo gedit /etc/apt/source.list" then remove the spaces between them, and run again, and see if the output is the same. If not, put a "#" in front of every line of anything that is coming up with a error.

---

### Post by hairchin67 on 2009-08-30
here is the result

gksudo gedit /etc/apt/source.list
[sudo] password for craig: 
E: Invalid operation updatesudo
craig@craig-desktop:~$ 




what now?

---

### Post by NoaHall on 2009-08-30
That was due to you typing wrong before hand :) Open a new terminal and do as my previous instructions said :)

---

### Post by hairchin67 on 2009-08-30
ok this source list is blank do i need to enter the corrected lines now ?

---

### Post by NoaHall on 2009-08-30
It's blank? Did you delete everything?

---

### Post by hairchin67 on 2009-08-30
its blank man!

---

### Post by NoaHall on 2009-08-30
Are you sure? Close it, don't save, and try opening it again.

---

### Post by hairchin67 on 2009-08-30
it still comes up blank can i fix this yet?

---

### Post by NoaHall on 2009-08-30
Here, use this [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) to replace your source.list

---

### Post by hairchin67 on 2009-08-30
i never added any sources manually so shouldnt the list indeed be blank? Ive always added updates without issue. why does all of a sudden this issue appear with my updates?

---

### Post by oboedad55 on 2009-08-30
> **NoaHall said:**
> It's blank? Did you delete everything?

Uh, it's sources.list. Plural. :KS

---

### Post by NoaHall on 2009-08-31
Doh! I was typing from a old windows laptop - I hate it.

try "gksudo gedit /etc/apt/sources.list"
and then follow my old instructions... sorry about that.

---

