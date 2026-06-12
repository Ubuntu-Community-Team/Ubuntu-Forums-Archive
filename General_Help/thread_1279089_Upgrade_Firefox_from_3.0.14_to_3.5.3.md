---
title: "Upgrade Firefox from 3.0.14 to 3.5.3"
date: 2009-09-30
forum: General Help
---

### Post by Rotax on 2009-09-30
I am new newbie to Ubuntu. Firefox has latest version is 3.5.3 and What I need to upgrade to 3.5.3 from 3.0.14? I have try Synaptic Package Manger with no Luck. When I select Firefox 3.5 as mark and then Apply. Then I click Firefox Icon at Panel and it still at 3.0.14.
Thanks

---

### Post by Megrimn on 2009-09-30
in linux, firefox 3.5 is codenamed 'shiretoko'.  Instead of clicking the firefox icon, try clicking the icon that looks like the earth.

---

### Post by madprofessor on 2009-09-30
Google search Ubuntuzilla. This will update Firefox. The problem with Shiretoko is the Firefox addons won't recognize it.

---

### Post by aysiu on 2009-09-30
Follow these instructions:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by lovinglinux on 2009-09-30
> **madprofessor said:**
> The problem with Shiretoko is the Firefox addons won't recognize it.

That's not true. Issues with extension on Shiretoko are probably due the extension not being compatible with version 3.5 or due to the fact that the extension author didn't update the compatibility declaration. Most of the time, you can override this without nasty consequences (see tutorial in my sig). Besides, it doesn't matter if you are running branded Firefox, Shiretoko, Iceweasel, Swiftfox, Swiftweasel. They are all compliant with Firefox extension API. So if an extension doesn't work with Shiretoko, it won't work with branded Firefox or the other alternative versions.

---

### Post by Yellow Pasque on 2009-09-30
Do not use physchocats or ubuntuzilla if you're on 64-bit Ubuntu. In fact, I see little reason not to just install the firefox-3.5 package and use that. As noted, it will be called Shiretoko and have a slightly different icon.

One more trick to make Shiretoko compatible with sites that check the user agent: start Shiretoko/FF 3.5 and enter about:config in the URL bar. Search for the general.useragent.extra.firefox key. Modify the *Shiretoko* part of this key to say Firefox. You may need to restart the browser for the change to take effect.

---

### Post by Rotax on 2009-09-30
> **Temüjin said:**
> Do not use physchocats or ubuntuzilla if you're on 64-bit Ubuntu. In fact, I see little reason not to just install the firefox-3.5 package and use that. As noted, it will be called Shiretoko and have a slightly different icon.

One more trick to make Shiretoko compatible with sites that check the user agent: start Shiretoko/FF 3.5 and enter about:config in the URL bar. Search for the general.useragent.extra.firefox key. Modify the *Shiretoko* part of this key to say Firefox. You may need to restart the browser for the change to take effect.

Been trying physchocat and ubuntuzilla, both too difficult for me. May try your hint. 
Where Shiretoko/FF 3.5 locate is at? ie: Appications/ADD and REMOVE that where FireFox appication there but it is Ubuntu package that is 3.0.14 and that is only one version 3.0.14. I have download Mozilla website and extract the files. Then use run shell within Firefox folder itself. But it doesn't remove older version. These I have try but could not locate where FireFox folder should storage file into which directory. Where is old Firefox directory is?

---

### Post by aysiu on 2009-10-01
> **Rotax said:**
> Been trying physchocat and ubuntuzilla, both too difficult for me. May try your hint. Watch the YouTube video on Psychocats. It isn't difficult. Highlight (with your mouse). Copy (with your mouse). Paste (with your mouse).

---

### Post by running_rabbit07 on 2009-10-01
> **aysiu said:**
> Watch the YouTube video on Psychocats. It isn't difficult. Highlight (with your mouse). Copy (with your mouse). Paste (with your mouse).

Then click, click, click on stuff with a smile. I think I have used the psychcat way of installing on almost every version of Ubuntu from Hardy to Jaunty, 32 bit and 64 bit. With Hardy 64 I had problems, but all else worked fine.

I currently use Shiretoko on Jaunty 64 without problems and next time I boot Debian, I am going to install 3.5 via the psychocat way. 

I also use Epiphany, because it looks better, but it has flaws with my college site.

---

### Post by aysiu on 2009-10-01
> **running_rabbit07 said:**
> Then click, click, click on stuff with a smile. I think I have used the psychcat way of installing on almost every version of Ubuntu from Hardy to Jaunty, 32 bit and 64 bit. With Hardy 64 I had problems, but all else worked fine. If it doesn't work on 64-bit, that's a shame. I don't have a 64-bit processor, so I can't test it myself, but the OP has not indicated 64-bit is an issue.

All I read was that Psychocats was "too difficult," which is ridiculous. It couldn't be simpler.

---

### Post by Rotax on 2009-10-01
yeah, way too difficult, beside my processor is not at 64.

---

### Post by aysiu on 2009-10-01
> **Rotax said:**
> yeah, way too difficult, beside my processor is not at 64. Great. If it isn't 64-bit, then I know Psychocats will work for you. It isn't for 64-bit.

Please explain to me what's difficult about it. If you can't highlight text and copy and paste it, I don't think any method is going to be easy for you.

---

### Post by running_rabbit07 on 2009-10-01
Doesn't ```
sudo apt-get install firefox-3.5
``` install Shiretoko? I can't remember if I did that way or the Syaptic way last time.


If you tried via the Synaptic way to install 3.5. Open a terminal and type ```
firefox-3.5
``` If that works, then it is installed and you just have to find the icon the Internet Menu.

---

### Post by running_rabbit07 on 2009-10-01
You may also try downloading the install file from mozilla.com and moving it from your desktop to your Home folder, then copy and paste this command in a terminal. ```
if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```A lot of wording there, but easy to copy and paste.

Which is pretty much the same thing the AYSIU's site says to do.

---

### Post by Rotax on 2009-10-01
> **Temüjin said:**
> Do not use physchocats or ubuntuzilla if you're on 64-bit Ubuntu. In fact, I see little reason not to just install the firefox-3.5 package and use that. As noted, it will be called Shiretoko and have a slightly different icon.

One more trick to make Shiretoko compatible with sites that check the user agent: start Shiretoko/FF 3.5 and enter about:config in the URL bar. Search for the general.useragent.extra.firefox key. Modify the *Shiretoko* part of this key to say Firefox. You may need to restart the browser for the change to take effect.

I got it, It is locate under Applications/Internet/Shiretoko Web Browser, but my bookmark is gone. And bookmark is still old version. But any way i may export bookmark and start using shiretoko. 

ps: I can make Shiretoko Web Browser to desktop icon and it is earth icon not same as Firefox icon. I see that. 

Thankyou very much for hint.

---

### Post by Rotax on 2009-10-01
my mistake, bookmark is valid and not gone. It work good. Thanks

---

