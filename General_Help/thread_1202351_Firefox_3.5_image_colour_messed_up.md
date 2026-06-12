---
title: "Firefox 3.5 image colour messed up"
date: 2009-07-02
forum: General Help
---

### Post by Crusty Juggler on 2009-07-02
For some reason, Firefox 3.5 has messed up colour in displaying images.  It has been this way since I tried RC2 through the final.  It doesn't happen with all images, just some.  I've tried searching for this problem elsewhere, but I'm not sure what to search.

In the attached, pic ff3 is firefox 3 ff35 is firefox 3.5

Any ideas/suggestions/fixes? 

Note: Image can be seen [here]("http://news.yahoo.com/nphotos/Home-Depot-job-security/photo//090630/480/cb9deb7fa65848b988bc73b0c636a248//s:/ap/20090702/ap_on_bi_go_ec_fi/us_economy") in case you want to check it yourself.

---

### Post by lovinglinux on 2009-07-02
It's because the color management is turned off. Type **about:config** in the address bar, accept the confirmation warning, then search for **gfx.color_management.enabled** and double click on it to toggle the value. It should be **true**. Restart Firefox.

---

### Post by push_back on 2009-07-02
Err... I'm having the same problem.  And there is no such option in my about:config.  
There's gfx.color_management.mode, which is an int and was set to 2.
And there's  gfx.color_management.rendering_intent, also an int, set to 0.  
I'll mess around with these, I guess.

[Edit]  ok, so setting  gfx.color_management.mode to 1 is an awful idea, but setting it to 3 seems to fix the problem for me

---

### Post by Zhao on 2009-07-02
> **push_back said:**
> Err... I'm having the same problem.  And there is no such option in my about:config.  
There's gfx.color_management.mode, which is an int and was set to 2.
And there's  gfx.color_management.rendering_intent, also an int, set to 0.  
I'll mess around with these, I guess.

[Edit]  ok, so **setting  gfx.color_management.mode** to 1 is an awful idea, but setting it **to 3** seems to fix the problem for me

Thanks, that worked for me too ;)

---

### Post by lovinglinux on 2009-07-02
> **push_back said:**
> Err... I'm having the same problem.  And there is no such option in my about:config.  
There's gfx.color_management.mode, which is an int and was set to 2.
And there's  gfx.color_management.rendering_intent, also an int, set to 0.  
I'll mess around with these, I guess.

[Edit]  ok, so setting  gfx.color_management.mode to 1 is an awful idea, but setting it to 3 seems to fix the problem for me

Usually when you don't have an option, you can create it. But I don't know if this option has been dropped, because I can't find a reference on Mozilla database, but it is on tutorials all over the web.

The options for **gfx.color_management.mode** are 0, 1 or 2. Check Mozilla Knowledge Database for [more info about this option](http://kb.mozillazine.org/Gfx.color_management.mode).

---

### Post by NoobixCube on 2009-07-29
I had this problem too.  Setting the colour management mode to 0 fixes it, once you restart Firefox.

---

### Post by lovinglinux on 2009-07-29
> **NoobixCube said:**
> I had this problem too.  Setting the colour management mode to 0 fixes it, once you restart Firefox.

See **Solution** [*[COLOR="Red"]**FOT007**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT007).

---

