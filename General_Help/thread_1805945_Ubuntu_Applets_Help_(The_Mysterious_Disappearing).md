---
title: "Ubuntu Applets Help (The Mysterious Disappearing)"
date: 2011-07-16
forum: General Help
---

### Post by johnnygabe89 on 2011-07-16
Hello Ubuntu forums!

I've searched everywhere, google, here, various sites, and i just can't seem to get a straight forward answer. So I'll be as specific and laymen terms  as possible.

I'm trying to fix my applets or indicators. In the top right of my window where the clock goes, the battery meter, wifi management, all that stuff. I seemed to have removed some of it on accident. When i right click the panel and select "add to panel" those options aren't there. I can't re-add what i removed. Also, the only way for me to get a battery meter and a wifi manager is thru the "indicator applet complete" which also comes with a completely useless and annoying envelope that doesn't do anything. Can I not just get the battery and wifi management icons and volume control icons? I also can't find the standard shut down icon, instead i get a huge red one, the only icon on the whole panel that's in colour. 

So whats the best solution for me? is there a outside program that handles applets, one that doesn't come with ubuntu? Also is there a way to download MORE applets and not just be limited to the default 15? 
Thanks in advance for the input and replies, I appreciate any and all help.

---

### Post by johnnygabe89 on 2011-07-17
Has anyone experienced this before?

---

### Post by Bleak888 on 2011-07-17
This explains how to add items to the panel. 

[https://help.ubuntu.com/community/Applets](https://help.ubuntu.com/community/Applets)

Personally I like having a dock. You should check out Docky.

---

### Post by johnnygabe89 on 2011-07-17
i know how to add items to the panel. my questions, or well problem lies with those items not being there to add. When i removed the applet from the panel by accident, it doesn't show back up on "add to panel".

---

### Post by Bleak888 on 2011-07-18
hmm. I guess I'm not understanding. When I click on the empty space on the panel, I am able to bring up all the default applets. There is also a search bar there. Even if I remove something from the panel, I can go back find it and install. 

I did find this link though on adding additional applets which may be helpful.

[http://news.softpedia.com/news/Top-10-Ubuntu-11-04-Unity-Panel-Applets-208034.shtml](http://news.softpedia.com/news/Top-10-Ubuntu-11-04-Unity-Panel-Applets-208034.shtml)

Good Luck!

---

### Post by CatKiller on 2011-07-18
Indicator Applet Complete is the one that you had before.

You can reset your panel configuration to the default with ```
gconftool --recursive-unset /apps/panel
```

---

### Post by trustinglittle on 2011-07-18
When you right click on the panel and click add to panel the Indicator Applet Complete object isn't there?

---

### Post by johnnygabe89 on 2011-07-18
okay say when i removed and applet from the panel and then go back to "add to panel" that applet wouldn't be there. What i ended up doing was just adding the Applet Complete and then going into terminal and removing the Me status deal and the evolution email. So now all i have in my Applet Complete is the battery meter, wifi manager, volume control, clock, and shut down. 
After searching the internet for a day i found a link to a website called ubuntu genius, where he showed you how to do this. Although, I really do appreciate all the advice and suggestions. Its nice knowing there is a forum in the world that will actually answer you back lol.
Once again, Thanks,
-John

---

### Post by dissembly on 2011-07-21
Hi all,

I have had the same problem, and I continue to have it after selecting "Indicator Applet Complete" - there is no longer any wireless management applet. There is the battery power indicator, the volume indicator, and the little envelope mail icon.

I also am sure that I used to be able to remove unwanted applets from the panel (I removed both the volume indicator and the mail icon), but selecting "remove from panel" only seems to allow me to remove everything under "Indicator Applet Complete" at once.

So my question is, where is the wireless management applet that I used to have? And where is the battery monitor applet that is independant of the volume and mail icons (i.e. not part of Indicator Applet Complete)?

(Also, i should mention because it was offered as an alternative solution, I don't want to use Docky - i find mac-style docks ugly; it's the reason I plan to skip 11.04.)

- David

edited to add: I've just noticed as well that it is no longer possible for me to left-click and drag some objects (time and date, for example), when I am sure it was before.

---

### Post by CatKiller on 2011-07-22
> **dissembly said:**
> it's the reason I plan to skip 11.04


Putting the network applet in the indicator system is new with 11.04. In earlier versions it was a Network Manager applet.
> 
edited to add: I've just noticed as well that it is no longer possible for me to left-click and drag some objects (time and date, for example), when I am sure it was before.

Middle-click & drag, unless it's locked to the panel. And unless it's many functions combined into one applet.

---

