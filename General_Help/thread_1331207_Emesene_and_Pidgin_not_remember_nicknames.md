---
title: "Emesene and Pidgin not remember nicknames"
date: 2009-11-19
forum: General Help
---

### Post by Woody1987 on 2009-11-19
When ever i set my nickname in emesene or pidgin it will forget it the next time i log on and sets it to my first name which i dont want. Empathy seems to work ok but unfortunately i dont like empathy and prefer to use emesene. Help appreciated.

---

### Post by zeli0726 on 2009-11-19
I have the same problem.
But it appeared only two days ago.

---

### Post by jpmelos on 2009-11-19
I have the same problem... It always sets my name back to my e-mail.

---

### Post by Woody1987 on 2009-11-21
Is there a solution to this yet?

---

### Post by sajiz on 2009-11-21
I have the same problem and until somebody finds a solution im gonna be using Galaxium Messenger instead

---

### Post by qwerty800 on 2009-11-22
Same here.

It's probably related to the configuration files.
As fas as I can see, my nick is registered nowhere in the configuration folder (/home/$USER/.config/emesene1.0)[Even if you use Emesene 1.5, it's still named 1.0].

I wonder if an update to Emesene 1.5.1 would fix that...

---

### Post by Joeasaurus on 2009-11-30
I'm having this problem aswell

its all set in the xml files which are in ~/.config/emesene1.0/<EMAIL>/cache/
I changed it and then when I logged in it was okay but after about 30 secs, it changed it back to my email again.

I don't know how to keep the changes permenant. I tried editing the config and then taking away right access for everyone but emesene threw an error and then managed to change my nivk back to my email again

Anyone else got a fix?

EDIT: I think it might be to do with the database file in that cache folder too but I tried opening it with sqlite and it failed because its encrypted

---

### Post by Leppie on 2009-11-30
There appears to be a problem with the ms servers. I've had the same issue in aMSN for a while now. Apparently we're pulling the nick info off the wrong server.
I don't think MS is very eager to resolve the issue... just be patient or change your first name on your profile page to what you want your nick to be. It's not a solution, but a workaround.

Hope this helps.

---

### Post by giovannisarto on 2009-12-10
There is a plugin called nicksaver.py for emesene that should apparently fix this problem, but i can't find a link where to download it. Has anyone an idea where i can find it?
Thanks!

---

### Post by sajiz on 2009-12-11
here is the plugin:

[http://go2.wordpress.com/?id=725X1342&site=elsoftwarelibre.wordpress.com&url=http%3A%2F%2Fblueorb.es%2Fwp-descargas%2FNickSaver.zip](http://go2.wordpress.com/?id=725X1342&site=elsoftwarelibre.wordpress.com&url=http%3A%2F%2Fblueorb.es%2Fwp-descargas%2FNickSaver.zip)


just unzip the file and copy it to

/home/USER/.config/emesene1.0/pluginsEmesene

then activate it through the plugin manager

---

### Post by andoni on 2009-12-15
The same is happening to me, I use Pidgin. I've just installed the latest Pidgin version, but the problem remains the same...

---

### Post by m0ar on 2009-12-27
FYI; Plugin doesn't work.


This one however, does:
[http://forum.emesene.org/index.php/topic,116.0.html](http://forum.emesene.org/index.php/topic,116.0.html)

---

### Post by Isengrin on 2010-01-01
Not solved in 1.5.1, but the plugin sajiz posted works perfect for me.

@m0ar
Isn't that plugin for something else? also, I think it comes by default now. :3

---

### Post by Jerther on 2010-01-04
Hi! I use Fedora 12 + Gnome but I had the same problem.

I moved from Kmess to emesene due to this problem because my girlfriend who's using Ubuntu and emesene didn't have it, but it looks like the problem is bound to my Live account.

However, I used the plugin provided by sajiz and finaly, FINALY, after all those hours trying to update kmess and giving up, at least emesene's working properly. Yeah, only a workaround, but at least I can focus on something else :)

THANK YOU

---

### Post by pistacoppu on 2010-01-08
installing the last version of pidgin solved that problem to me.
But i still have it with emesene (no plugin), i think we have to wait 1.6 to have that solved; there are some fixes that we will have in 1.6:

"With loads of bugfixes, gui awesomeness and the new year here comes the new release of your beloved msn client:

    * Improved gui usability
    * New preference window (arielj, ukblacknight, nicolaide, mehd36)
    * Implemented nick and personal message roaming (pablo)
    * Fixed tons of bugs all around the code (we're too lazy to write 'em all)  "
from emesene.org

---

### Post by pistacoppu on 2010-01-10
If you use Pidgin 2.6.4 or emesene 1.6 you won't have that problem anymore

---

### Post by TenTin on 2010-06-18
Really? I'm using 1.6.1 now, and there is still this error, giving me the nick and pm that I last used on my ipod touch, though I already tried to change it on emesene but to no avail.:-k

---

