---
title: "BBC Iplayer does.... nothing. how do I go about fixing it?"
date: 2011-02-10
forum: General Help
---

### Post by jezzah on 2011-02-10
I tried installing bbc iplayer from [http://www.bbc.co.uk/iplayer/install](http://www.bbc.co.uk/iplayer/install) On Xubuntu 10.10.

It gave me an icon on my desktop that on a double click does nothing :(

If I run '/opt'/'BBC iPlayer Desktop'/bin/'BBC iPlayer Desktop' from the command line I get the following output.

> '/opt'/'BBC iPlayer Desktop'/bin/'BBC iPlayer Desktop'
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:86: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:134: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:187: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:243: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:288: Murrine configuration option "gradients" is no longer supported and will be ignored.

And then nothing else happens.

I figured this output is probably irrelevant... How should I go about getting iplayer desktop to work? The iplayer help was sadly lacking.

On Googling I found somebody mention the following worked for them.
```
 sudo apt-get install gnome-keyring '(was already installed apparently)
 export GNOME_DESKTOP_SESSION_ID='xfce'
 '/opt'/'BBC iPlayer Desktop'/bin/'BBC iPlayer Desktop
```
Nothing changed when I tried this.

Cheers for any replies.

---

### Post by MickS on 2011-02-10
I think there is a problem at the BBC end, I was watching it an hour ago but now it isn't working for me either, so I would suggest you do nothing until tomorrow.

---

### Post by jezzah on 2011-02-10
> **MickS said:**
> I think there is a problem at the BBC end, I was watching it an hour ago but now it isn't working for me either, so I would suggest you do nothing until tomorrow.

No you don't understand, the program won't launch. 
This has been going on for more than a day - it does not look like a remote issue.

I also noticed that "Adobe air application launcher" has the same symptoms (clicking it does nothing to the same warnings). I'm guessing whatever is going wrong is something wrong with adobe air... So I tried uninstalling adobe air and re-installing their latest version for their website as opposed to the lower version on the ubuntu software centre... This didn't fix any issues :(, but it gives me something to go on.

---

### Post by tredegar on 2011-02-10
Much of the BBC iplayer content is not available outside the UK.

This is right as we are paying for it, perhaps you are not.

What country are you in?

---

### Post by MickS on 2011-02-11
Sorry I misunderstood you, I watch iplayer with Firefox mostly and use get_iplayer for downloading stuff, never bothered with the Adobe thing.

---

