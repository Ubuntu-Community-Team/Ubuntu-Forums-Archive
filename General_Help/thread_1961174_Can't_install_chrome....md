---
title: "Can't install chrome..."
date: 2012-04-18
forum: General Help
---

### Post by Beastboy26 on 2012-04-18
I am using the software install app, can't install chrome, I get this fail message: 

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-codecs-ffmpeg_17.0.963.79~r125985-0ubuntu0.11.10.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-codecs-ffmpeg_17.0.963.79~r125985-0ubuntu0.11.10.1_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser_17.0.963.79~r125985-0ubuntu0.11.10.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser_17.0.963.79~r125985-0ubuntu0.11.10.1_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]

I thinking I may need to change my repostiorys, but to what?

---

### Post by zdeuyo on 2012-04-18
Hello,


Try installing Google Chrome not Chromium.

Link: [https://www.google.com/chrome]("https://www.google.com/chrome")

Hope this helps.

---

### Post by tmaranets on 2012-04-18
I had a problem like that before. Try letting Ubuntu rest by not trying the download for some time. Then try the Chromium download, it should work.

---

### Post by lisanels47 on 2012-04-18
apt-get update && apt-get -y install chromium-browser

Should work fine.  I run Chromium all the time.

---

### Post by fiatveritas on 2012-04-18
On my system I had to move to the directory I saved my google-chrome file and run ```
sudo dpkg -i google-chrome(filename).deb
``` Then the terminal instructed me to use ```
apt-get -f install
```After which, google-chrome installed itself.

---

### Post by MonkeyPaw on 2012-04-18
You can just use Chromium from the Software Center. It's pretty much identical to Chrome--sync, extensions, appearance, etc. You will have a hard time telling the difference.

---

