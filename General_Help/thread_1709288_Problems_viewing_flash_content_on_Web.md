---
title: "Problems viewing flash content on Web"
date: 2011-03-18
forum: General Help
---

### Post by AndrewGen on 2011-03-18
I suddenly find myself unable to view video content from the web.  I'm not sure what changed, other than installing the recommended updates to Ubuntu about a week ago.  

I'm thinking a Flash update/reinstall might resolve the problem, but I can't seem to get the updates to install properly.  (Guess I need help using terminal).

Any suggestions?  Thanks.

---

### Post by Shmantiv_Radio on 2011-03-18
> **AndrewGen said:**
> I suddenly find myself unable to view video content from the web.  I'm not sure what changed, other than installing the recommended updates to Ubuntu about a week ago.  

I'm thinking a Flash update/reinstall might resolve the problem, but I can't seem to get the updates to install properly.  (Guess I need help using terminal).

Any suggestions?  Thanks.

Try this in the Terminal.

```
sudo apt-get purge -f flashplugin-installer adobe-flashplugin flashplugin-nonfree
```Then download and install this.

[http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.2_for_Linux_(.deb)]("http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.2_for_Linux_%28.deb%29")

---

### Post by AndrewGen on 2011-03-18
> **Shmantiv_Radio said:**
> Try this in the Terminal.

```
sudo apt-get purge -f flashplugin-installer adobe-flashplugin flashplugin-nonfree
```Then download and install this.

[http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.2_for_Linux_(.deb)]("http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.2_for_Linux_%28.deb%29")


Thanks,

That helped with the some content, such as ads on various sites, but not with videos like news clips on Yahoo or CNET videos.  Any other suggestions?

Thanks again.

---

### Post by Vaphell on 2011-03-18
what is your issue exactly?
either way check if disabling hardware acceleration in flash settings helps
go to [http://derbauer.de](http://derbauer.de) (has settings menu enabled), rightclick, settings

---

### Post by 5149.5 on 2011-03-18
Have you checked flashaid?

[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

---

### Post by akakingess on 2011-03-18
+1 on Flashaid, it has done wonders for my experiences with the troubles I used to have with Flash...

---

### Post by AndrewGen on 2011-03-18
> **Vaphell said:**
> what is your issue exactly?
either way check if disabling hardware acceleration in flash settings helps
go to [http://derbauer.de](http://derbauer.de) (has settings menu enabled), rightclick, settings

When I try to view any video from the web, I get a blank black screen.

---

### Post by AndrewGen on 2011-03-18
> **5149.5 said:**
> Have you checked flashaid?

[https://addons.mozilla.org/en-us/firefox/addon/flash-aid/](https://addons.mozilla.org/en-us/firefox/addon/flash-aid/)

That did it. !!!

Thanks for the advice.

---

