---
title: "How to type in Japanese using Karmic Koala?"
date: 2009-11-06
forum: General Help
---

### Post by haragatatsu on 2009-11-06
I've perused some posts on installing Japanese language fonts for earlier versions of Ubuntu but I'm still kinda lost.  I want to type in japanese characters while using the internet.  I'm using Karmic Koala.

I did this in a term window:  sudo apt-get install scim

I also clicked on Japanese in the "install/remove languages" section within system/admin/language support. 

But that's about it -- what else do I need to do?  

Yoroshiku!

---

### Post by bapoumba on 2009-11-08
Moved to General Help.

---

### Post by Irihapeti on 2009-11-08
You may need to install some additional packages. I'm assuming that you are using Gnome and not KDE. Type in a terminal:

```
sudo apt-get install scim-bridge-client-gtk
sudo apt-get install scim-anthy
```

Anthy is a popular method for inputting Japanese characters.

It's possible that these packages were installed when you installed the Japanese language files. If so, apt-get will tell you.

Then open the language support utility (System -> Administration -> Language Support) and choose "scim-bridge" in the Keyboard input method system box. Log out and in again.

Open a document such as the text editor, and press control-space. You should get a small panel appear at the bottom right hand corner of the screen. You can then press control-shift to toggle through the input methods available.

For more precise setting up, use the Scim Input Method Setup under System -> Preferences

---

### Post by riesengreen on 2009-11-08
> **Irihapeti said:**
> You may need to install some additional packages. I'm assuming that you are using Gnome and not KDE. Type in a terminal:

```
sudo apt-get install scim-bridge-client-gtk
sudo apt-get install scim-anthy
```

Anthy is a popular method for inputting Japanese characters.

It's possible that these packages were installed when you installed the Japanese language files. If so, apt-get will tell you.

Then open the language support utility (System -> Administration -> Language Support) and choose "scim-bridge" in the Keyboard input method system box. Log out and in again.

Open a document such as the text editor, and press control-space. You should get a small panel appear at the bottom right hand corner of the screen. You can then press control-shift to toggle through the input methods available.

For more precise setting up, use the Scim Input Method Setup under System -> Preferences
Irihapeti-san:

&#12393;&#12358;&#12418;&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12375;&#12383;&#12290;

&#12392;&#12390;&#12418;&#20998;&#12363;&#12426;&#12420;&#12377;&#12363;&#12387;&#12383;&#12391;&#12377;&#12290;

Ben

---

### Post by mdurham on 2009-11-08
I would remove the SCIM based stuff as it's (I read) no longer supported or updated. The thing to use is iBus.
Administration->Language-Support, Keyboard&InputMethod select ibus. I haven't tried it on Japanese but it's a great improvement with simplified Chinese. It just works!
Cheers, Mike

---

### Post by Irihapeti on 2009-11-08
I get the impression that Scim may be phased out in future releases. However, if Scim is in the repositories, it will be maintained for the duration of the release. If it's doing what the user wants it to, I see no reason to remove it.

iBus is fairly new and some people have had problems with it. Ultimately, it comes down to personal preference.

In karmic, you can even have both installed at once and use the Language Support utility to switch between the two. All you need to do is log out and in again.

@riesengreen

Unfortunately, I don't know any Japanese. You'll have to translate for me. (I'm a beginner at Mandarin Chinese.)

Irihapeti

---

### Post by haragatatsu on 2009-11-10
&#25104;&#21151;!  (success!)  Thanks to Irihapeti for the code on loading anthy, which turned out to do the trick.  And merci to bapoumba for approving the thread:D  Having to type in gedit first and then cut and paste the text into an online website is kind of a hassle though.  But it's better than no ability at all . . . .

Ben's note to Irihapeti translates as "thank you very much.  It was very easy to understand."

Now, if I could only get some help with my sound problems . . . .

---

### Post by Irihapeti on 2009-11-10
&#19981;&#23458;&#27668;&#12290; (You're welcome.) I'm glad to know that it's worked.

---

### Post by nomnex on 2010-02-06
> **Irihapeti said:**
> 

Then open the language support utility (System -> Administration -> Language Support) and choose "scim-bridge" in the Keyboard input method system box. Log out and in again.

Thanks, that was the missing information to get it work.

mdurham (post #5), I am currently using iBus-anthy and I like it better. on Karmic, when you install SCIM-anthy, + Japanese; iBus, iBus-anthy is automatically installed along the way. Never heard of ibus before reading you comment. Thank you.

---

### Post by mdurham on 2010-02-06
Yes iBus is the way to go, it's a much easier & cleaner system. I don't think that any SCIM stuff is needed when using iBus.

---

### Post by saxman66 on 2010-04-03
One of the problems that I am having is getting to the point where I can get to scim-bridge under keyboard input. I can get to language support but all I see is a bunch of languages. When I go to Japanese, all I get is a couple of options that have nothing to do with this.

Then open the language support utility (System -> Administration -> Language Support) and choose "scim-bridge" in the Keyboard input method system box.

---

