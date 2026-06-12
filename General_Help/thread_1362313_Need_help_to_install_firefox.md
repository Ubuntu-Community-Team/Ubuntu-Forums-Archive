---
title: "Need help to install firefox"
date: 2009-12-23
forum: General Help
---

### Post by dhanabalan_svks on 2009-12-23
Hi Dears,

i need ur help to install firebox.
i am trying to install firefox via synaptic packaage manager.I get following error.
I am using ubunthu 9.04 jaunty ..

[B]firefox-3.5:
 Depends: xulrunner-1.9.1 but it is not going to be installed
 Depends: firefox-3.5-branding but it is not going to be installed or
     abrowser-3.5-branding but it is not going to be installed
 Recommends: ubufox but it is not going to be installed
[/B]

also i was not able to install firefox previous versions 3.0 ...
please help me to install.

thanks,
Dhanabalan.c
 		                   		  		  		 		 			 				__________________
				Dhanabalan.cs

---

### Post by HappyFeet on 2009-12-23
Go to system>administration>software sources and check to see if all boxes are checked.

---

### Post by SchizmWolf on 2009-12-23
Have you tried to use Ubuntu's aptitude?

Open terminal --> sudo apt-get install firefox

That worked fine for me and took all of 2 minutes from start to finish.
Otherwise you can dl firefox in a .deb package. With jaunty 9.04 you should be able to double-click it and just hit "install" when the prompt pops up.

Hope that helps.:)

---

### Post by dhanabalan_svks on 2009-12-23
i am using sudo apt-get install firefox in my terminal But i get following error 

[B]The following packages have unmet dependencies:
  firefox: Depends: firefox-3.5 but it is not going to be installed
           Depends: firefox-3.5-branding but it is not going to be installed
E: Broken packages
[/B]

Thanks,
Dhanabalan.c

---

### Post by dhanabalan_svks on 2009-12-23
> **HappyFeet said:**
> Go to system>administration>software sources and check to see if all boxes are checked.

yea ,

 all are checked , but nothing happened.
 help me ..

Thanks,
Dhanabalan.c

---

### Post by running_rabbit07 on 2009-12-23
Is the Firefox listed in your Synaptic Package Manager? If so, does it give the same errors?

---

### Post by lavinog on 2009-12-23
try and install firefox-3.5 and firefox-3.5-branding

also did you do what happyfeet mentioned?

---

### Post by dhanabalan_svks on 2009-12-23
> **running_rabbit07 said:**
> Is the Firefox listed in your Synaptic Package Manager? If so, does it give the same errors?

Yes in my synaptic package manager some firefox version are listed they are 3.0,3.1,3.2,3.5

if i am trying to install 3.0 ,it give following error message
[B]
firefox-3.0:
 Depends: firefox-3.5 but it is not going to be installed[/B]

Thanks,
Dhanabalan.c

---

### Post by SchizmWolf on 2009-12-23
Not sure if this will fix it, but it's worth a shot

Terminal---> sudo apt-get -f install firefox

The appended -f might be able to fix it. Still lookin' though

---

### Post by running_rabbit07 on 2009-12-23
If the above doesn't fix it, the only work around I can think of is to install via this [method]("http://www.psychocats.net/ubuntu/firefox") from the mozilla site.

---

### Post by dhanabalan_svks on 2009-12-23
> **SchizmWolf said:**
> Not sure if this will fix it, but it's worth a shot

Terminal---> sudo apt-get -f install firefox

The appended -f might be able to fix it. Still lookin' though


No dear,
still i get the following error

[B]The following packages have unmet dependencies:
  firefox: Depends: firefox-3.5 but it is not going to be installed
           Depends: firefox-3.5-branding but it is not going to be installed
E: Broken packages
[/B]

---

### Post by SchizmWolf on 2009-12-23
Well, then, I'd suggest following running_rabbit07's advice and visiting the linked site. I've copied the terminal input directly from the site and will post it below, but still check it out.

Terminal---> if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox

that should individually download all the necessary components of firefox individually.

---

### Post by lavinog on 2009-12-23
> **SchizmWolf said:**
> Well, then, I'd suggest following running_rabbit07's advice and visiting the linked site. I've copied the terminal input directly from the site and will post it below, but still check it out.

Terminal--->```
 if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

that should individually download all the necessary components of firefox individually.
Please use code tags for terminal commands

---

### Post by SchizmWolf on 2009-12-23
> **lavinog said:**
> Please use code tags for terminal commands

My apologies, I'm new to the forum, still getting the gist of everything. I'll not clutter in the future.:oops:

---

### Post by running_rabbit07 on 2009-12-23
> **SchizmWolf said:**
> My apologies, I'm new to the forum, still getting the gist of everything. I'll not clutter in the future.:oops:
I will use spaces to make it easier. to do the code thing [ code ] at the begining and [/ code ] at the end. Not a problem though. Just take out the spaces between the lettering and the []s.

---

### Post by SchizmWolf on 2009-12-23
> **running_rabbit07 said:**
> I will use spaces to make it easier. to do the code thing [ code ] at the begining and [/ code ] at the end. Not a problem though. Just take out the spaces between the lettering and the []s.
Thanks ^.^ that helps me a lot!

---

### Post by lavinog on 2009-12-23
> **running_rabbit07 said:**
> I will use spaces to make it easier. to do the code thing [ code ] at the begining and [/ code ] at the end. Not a problem though. Just take out the spaces between the lettering and the []s.

for future reference, you can use [noparse][noparse][/noparse][/noparse] tags instead of adding spaces:
[noparse][noparse]```
stuff
```[/noparse][/noparse]
yields:
[noparse]```
stuff
```[/noparse]

---

### Post by bodhi.zazen on 2009-12-23
Try update first :

```
sudo apt-get update && sudo apt-get install firefox
```

---

