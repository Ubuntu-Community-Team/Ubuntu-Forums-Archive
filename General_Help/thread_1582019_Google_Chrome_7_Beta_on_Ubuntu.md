---
title: "Google Chrome 7 Beta on Ubuntu"
date: 2010-09-25
forum: General Help
---

### Post by TheNerdAL on 2010-09-25
I would like to install Google Chrome 7 on Ubuntu to try it out. How can I do this?

---

### Post by lovexp on 2010-09-25
> **TheNerdAL said:**
> I would like to install Google Chrome 7 on Ubuntu to try it out. How can I do this?

Chromium for Ubuntu could be found in the following PPAs:


+ [https://launchpad.net/~chromium-daily/+archive/stable](https://launchpad.net/~chromium-daily/+archive/stable) (Stable Channel)
+ [https://launchpad.net/~chromium-daily/+archive/beta](https://launchpad.net/~chromium-daily/+archive/beta) (Beta Channel)
+ [https://launchpad.net/~chromium-daily/+archive/dev](https://launchpad.net/~chromium-daily/+archive/dev) (Dev Channel)
+ [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa) (trunk/daily builds)

---

### Post by mrhhug on 2010-09-25
absolutly, if you add google's repositories to your /etc/apt/sources.list file every time your system updates it will update anything installed through apt

heres a site; [http://www.google.com/linuxrepositories/testrepo.html](http://www.google.com/linuxrepositories/testrepo.html)
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```
```
echo "deb http://dl.google.com/linux/deb/ stable non-free" | sudo tee -a /etc/apt/sources.list
```
```
echo "deb http://dl.google.com/linux/deb/ testing non-free" | sudo tee -a /etc/apt/sources.list
```
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
```
```
sudo aptitude upgrade
```
```
sudo aptitude install google-chrome
```

your off!!! just hit alt+f2 then type in google-chrome


or you can just go to google and type in install chrome, and it will point you to a way to download a .deb and you can install that way (no apt updating though)

actually google made it REALLY easy [http://www.google.com/linuxrepositories/scripted.html](http://www.google.com/linuxrepositories/scripted.html)

---

### Post by TheNerdAL on 2010-09-25
> **mrhhug said:**
> absolutly, if you add google's repositories to your /etc/apt/sources.list file every time your system updates it will update anything installed through apt

heres a site; [http://www.google.com/linuxrepositories/testrepo.html](http://www.google.com/linuxrepositories/testrepo.html)
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```
```
echo "deb http://dl.google.com/linux/deb/ stable non-free" | sudo tee -a /etc/apt/sources.list
```
```
echo "deb http://dl.google.com/linux/deb/ testing non-free" | sudo tee -a /etc/apt/sources.list
```
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
```
```
sudo aptitude upgrade
```
```
sudo aptitude install google-chrome
```

your off!!! just hit alt+f2 then type in google-chrome


or you can just go to google and type in install chrome, and it will point you to a way to download a .deb and you can install that way (no apt updating though)

actually google made it REALLY easy [http://www.google.com/linuxrepositories/scripted.html](http://www.google.com/linuxrepositories/scripted.html)

I want the Beta of Google Chrome 7 not the Stable of Google Chrome 7. And I don't want Chromium.

---

### Post by mrhhug on 2010-09-25
not a problem 
```
sudo aptitude install google-chrome-beta
```

its in the stable non-free main repos

---

### Post by luceerose on 2010-09-25
Add key in terminal;
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```
gksu gedit /etc/apt/sources.list
& add these 2 lines;
```
deb http://dl.google.com/linux/deb/ stable non-free main 
deb http://dl.google.com/linux/deb/ testing non-free main
```
There are 3 different packages. You can only install one at a time.
google-chrome-stable, google-chrome-beta & google-chrome-unstable.
The package for version 7 is the 'google-chrome-unstable' package.

PS. I have to say, I haven't found it to be particularly "unstable" so far. I'm running the beta on 2 computers & the unstable on the other 2. I'm really happy with both versions. I have the Chromium beta installed as well, as a backup browser.

The stable version (last time I checked) couldn't sync extensions. That's what makes version 6 so much better. The only difference I've noticed so far between 6 & 7 is the RAM usage has gone down slightly since version 6.

---

### Post by bodhi.zazen on 2010-09-25
See also :

[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

read the entire link :

> **Note: **Installing Google Chrome will **add the Google repository** so your system will automatically keep Chrome up to date.So you can install the .deb from that site.

---

### Post by mrhhug on 2010-09-25
> **bodhi.zazen said:**
> See also :

[http://dev.chromium.org/getting-involved/dev-channel](http://dev.chromium.org/getting-involved/dev-channel)

read the entire link :

[quote}**Note: **Installing Google Chrome will **add the Google repository** so your system will automatically keep Chrome up to date.

So you can install the .deb from that site.[/QUOTE]

good catch!

---

### Post by TheNerdAL on 2010-09-25
> **larsenguitars said:**
> Add key in terminal;
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```
gksu gedit /etc/apt/sources.list
& add these 2 lines;
```
deb http://dl.google.com/linux/deb/ stable non-free main 
deb http://dl.google.com/linux/deb/ testing non-free main
```
There are 3 different packages. You can only install one at a time.
google-chrome-stable, google-chrome-beta & google-chrome-unstable.
The package for version 7 is the 'google-chrome-unstable' package.

PS. I have to say, I haven't found it to be particularly "unstable" so far. I'm running the beta on 2 computers & the unstable on the other 2. I'm really happy with both versions. I have the Chromium beta installed as well, as a backup browser.

The stable version (last time I checked) couldn't sync extensions. That's what makes version 6 so much better. The only difference I've noticed so far between 6 & 7 is the RAM usage has gone down slightly since version 6.

This worked but I saw a video where Google Chrome 7 Beta has Side Tabs and I want that but it doesn't show up when I right click a tab. :(

---

### Post by luceerose on 2010-09-25
Side Tabs...
Interesting.
Haven't seen that. I'll just do some quick research.

---

### Post by mrhhug on 2010-09-25
> This worked but I saw a video where Google Chrome 7 Beta has Side Tabs and I want that but it doesn't show up when I right click a tab. :(

like this? [http://www.downloadsquad.com/2010/07/22/how-to-enable-side-tabs-in-google-chrome/](http://www.downloadsquad.com/2010/07/22/how-to-enable-side-tabs-in-google-chrome/)

sorry not for us yet : ( [http://src.chromium.org/viewvc/chrome?view=rev&revision=57635](http://src.chromium.org/viewvc/chrome?view=rev&revision=57635)

---

### Post by TheNerdAL on 2010-09-25
> **mrhhug said:**
> like this? [http://www.downloadsquad.com/2010/07/22/how-to-enable-side-tabs-in-google-chrome/](http://www.downloadsquad.com/2010/07/22/how-to-enable-side-tabs-in-google-chrome/)

sorry not for us yet : ( [http://src.chromium.org/viewvc/chrome?view=rev&revision=57635](http://src.chromium.org/viewvc/chrome?view=rev&revision=57635)

Noooo!!!!!!! ):

---

### Post by luceerose on 2010-09-25
There's an extension called VerticalTabs
I think that might be what you're after.

---

### Post by luceerose on 2010-09-25
For some reason the '--enable-vertical-tabs' switch doesn't work for me in v7.0.517.13

---

### Post by TheNerdAL on 2010-09-25
> **larsenguitars said:**
> For some reason the '--enable-vertical-tabs' switch doesn't work for me in v7.0.517.13

I never knew you could do that in the first place.

---

### Post by luceerose on 2010-09-25
Looks like it only works in the windows version so far. Pity.
This is another switch I recommend using. It stops junk from building up on the hard drive;
--disk-cache-size=1 --media-cache-size=1

Also, I use a nice set of extensions that I've found work rather well to keep away the nasties;
AdBlock, Better Pop Up Blocker, WOT

---

### Post by TheNerdAL on 2010-09-25
Well, thanks anyways for the instructions on how to install Google Chrome 7. :)

---

