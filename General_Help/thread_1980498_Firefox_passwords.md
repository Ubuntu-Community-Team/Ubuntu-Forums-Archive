---
title: "Firefox passwords"
date: 2012-05-15
forum: General Help
---

### Post by Spitted on 2012-05-15
Hello

For some reason, on my laptop, firefox never remembers any passwords I type in browser forms - for example gmail, ubuntu forums, etc. 
It happens both on 11.10 and 12.04, with the default firefox (I haven't changed any settings).

What can I do? :confused:

Thanks,
Eyal

---

### Post by SuaSwe on 2012-05-15
Hi Eyal,

Have you checked in Edit > Preferences that "Remember Passwords for Sites" is ticked (with the sites you want it to save passwords for not present in the exceptions list)? A couple of other random and possibly irrelevant things coming to mind would be ensuring that you don't have private browsing ticked (under Tools), and that you have appropriate permissions of the profiles folder (located under /.mozilla/firefox/, called something like 12abcde3.default). 

Do other browsers save passwords? Does Firefox offer to save them then fail to, or does it not even attempt to?

---

### Post by Dngrsone on 2012-05-15
Go to Edit/Preferences/Security and make sure the checkbox 'Remember Passwords for sites' is enabled.

I use the LastPass plugin for firefox, myself; it makes my password set portable (though I normally don't rely on the cloud, if I need passwords for websites, then I am already connected to the internet, neh?).

---

### Post by SeijiSensei on 2012-05-15
If the browser is set to remember passwords, it's possible that it remembered an empty or incorrect password at some point.  You can reviewed your stored passwords and delete sites that don't work.  When you reconnect to the site, you'll be prompted to store the correct password once again.

---

### Post by Spitted on 2012-05-15
Thanks for all you comments guys.
Here is some info about my problem:
I'm running Firefox 12.0 official ubuntu release.
"Remember Passwords for Sites" is ticked.
The exceptions list is empty.
The saved passwords list is empty.
Firefox does NOT ask me to save passwords (although I always tick the checkbox when available on forms).
I found the profiles folder, it contains many files, but I'm not sure what kind of permissions I should look for.
And finally something weird - 
Under Tools I have an option to "Stop Private Browsing" (indicating it is currently active) but it is greyed out, meaning I cannot click it! It might be the cause of all this...

Another thing - I tried Midori and it saves my passwords correctly

---

### Post by GreatDanton on 2012-05-15
For many years I thought how good Firefox browser is. But then I met the same problem, and I couldn't solve it. Sometimes re-install helps sometimes not. Then I tried Opera and I can proudly say that Opera is one of the best browser out there (in my opinion). It's also much faster than firefox (why is so I don't know), and yes it saves passwords :).

If I were you, I would give Opera a try and pick the browser you like. Also you should try Chromium, I heard very good things about it, but I stick to Opera, because of Google (Google own Chromium).

Hope this helps!

---

### Post by Spitted on 2012-05-15
Yeah, I too don't want to use Chromium because of Google.
I have never tried Opera. Maybe I'll give it a chance. But still I really really like Firefox, especially the current direction it takes, so I'll be glad if I can work this thing out...

---

### Post by Dngrsone on 2012-05-15
Your username should be the owner and group for the entire .mozilla folder.  If it is different, then that might be your problem.

---

### Post by Spitted on 2012-05-15
> **Dngrsone said:**
> Your username should be the owner and group for the entire .mozilla folder.  If it is different, then that might be your problem.
That is indeed the case. And still no solution... :(

---

### Post by Enigmapond on 2012-05-15
> **Spitted said:**
> Yeah, I too don't want to use Chromium because of Google.
I have never tried Opera. Maybe I'll give it a chance. But still I really really like Firefox, especially the current direction it takes, so I'll be glad if I can work this thing out...

Try Iron browser then. Same code as Chromium with no calling home to Google...unless you want it to.

[http://www.srware.net/en/software_srware_iron_download.php]("http://www.srware.net/en/software_srware_iron_download.php")

---

### Post by SuaSwe on 2012-05-16
Have you had a look at [this solution]("http://forums.mozillazine.org/viewtopic.php?f=38&t=2148803")? There is an option to set permanent private browsing that may be enabled. (I don't seem to have the same option on mine however it looks like "never remember history" might do the same thing - perhaps ensure that it's set to remember history?)

If this fails, try a web search for "can't turn off private browsing Firefox" or similar, it seems to be a pretty common issue. :)

---

