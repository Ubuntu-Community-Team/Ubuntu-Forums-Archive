---
title: "problem using a website.........Content Encoding Error"
date: 2011-12-19
forum: General Help
---

### Post by monstrous behaviour on 2011-12-19
Hi,

Sorry for beginning with a problem............isn't it often the way?

One website is causing me problems.........and no other user is reporting issues........

Sometimes I'm presented with reams of html........sometimes I get the following errors:

  -  "Error 330 (net::ERR_CONTENT_DECODING_FAILED): Unknown error." - when using Chrome.

-  "Content Encoding Error  -  The page you are trying to view cannot be shown because it uses an invalid or unsupported form of compression." - when using, as I usually do, FF.  I've tried clearing the cache in FF

I'm running Oneiric and FF 8 (FF for Ubuntu canonical 1.0 - on the update channel).

Only one site gives me problems.  But no other users report an issue.  :confused:   Instinctively I've been faffing on in FF.  I have disabled add-ons - no improvement.  Is it something to do with Ubuntu!?!  :confused:

All advice welcomed.  :D

---

### Post by fdrake on 2011-12-19
can you post the url of the site , maybe there is just an error in the page..

---

### Post by lovinglinux on 2011-12-19
I think it is a server side issue, not in your browser.

---

### Post by monstrous behaviour on 2011-12-19
> **lovinglinux said:**
> I think it is a server side issue, not in your browser.
hi - from my work pc i had no problem.............

so I'm assuming it's my laptop/os causing the issue?

---

### Post by lovinglinux on 2011-12-19
> **monstrous behaviour said:**
> hi - from my work pc i had no problem.............

so I'm assuming it's my laptop/os causing the issue?

Did you use the same version of Firefox and Ubuntu? I am asking this because I was helping another user experiencing issues with aspx pages being downloaded instead of rendered. The problem only happens on Ubuntu with Firefox 8+, because the site doesn't recognize the user agent properly. I am not sure if this is the case, but it could be.

I have experienced the same problem you are experiencing now, but I really don't remember in which conditions it happened.

---

### Post by monstrous behaviour on 2011-12-20
> **lovinglinux said:**
> Did you use the same version of Firefox and Ubuntu? I am asking this because I was helping another user experiencing issues with aspx pages being downloaded instead of rendered. The problem only happens on Ubuntu with Firefox 8+, because the site doesn't recognize the user agent properly. I am not sure if this is the case, but it could be.

I have experienced the same problem you are experiencing now, but I really don't remember in which conditions it happened.

Hi - at work I was on Windows and IE - seemed to have no issues.

At home I tried using Windows / FF and Ubuntu/FF and also Ubunu/Chrome

I tried from different accounts on the same home laptop.  Nobody using the site is complaining other than me.  Weird!

:confused:

---

### Post by lovinglinux on 2011-12-20
> **monstrous behaviour said:**
> Hi - at work I was on Windows and IE - seemed to have no issues.

At home I tried using Windows / FF and Ubuntu/FF and also Ubunu/Chrome

I tried from different accounts on the same home laptop.  Nobody using the site is complaining other than me.  Weird!

:confused:

Can you post the url?

---

### Post by monstrous behaviour on 2011-12-20
> **lovinglinux said:**
> Can you post the url?

of course

[http://www.alfaowner.com]("http://www.alfaowner.com/aohome.php")

---

### Post by lovinglinux on 2011-12-20
> **monstrous behaviour said:**
> of course

[http://www.alfaowner.com]("http://www.alfaowner.com/aohome.php")

I am unable to reproduce the problem, with FF 8 or 10. I will keep trying.

---

### Post by monstrous behaviour on 2011-12-20
> **lovinglinux said:**
> I am unable to reproduce the problem, with FF 8 or 10. I will keep trying.
cheers

much appreciated

I've tried it on my home laptop in windows and ubuntu and in firefox and chrome in both set-ups......causes problems every time, on this one site alone.

Incredibly frustrating.

---

### Post by lovinglinux on 2011-12-21
> **monstrous behaviour said:**
> cheers

much appreciated

I've tried it on my home laptop in windows and ubuntu and in firefox and chrome in both set-ups......causes problems every time, on this one site alone.

Incredibly frustrating.

The problem happens all the time?

Try changeing the user agent with [User Agent RG](https://addons.mozilla.org/en-US/firefox/addon/user-agent-rg/) extension.

---

### Post by monstrous behaviour on 2011-12-28
> **lovinglinux said:**
> The problem happens all the time?

Try changeing the user agent with [User Agent RG](https://addons.mozilla.org/en-US/firefox/addon/user-agent-rg/) extension.

Hi - i think I installed that, but I'm out of my depth here and wasn't sure what to do next. sorry

---

### Post by lovinglinux on 2011-12-30
> **monstrous behaviour said:**
> Hi - i think I installed that, but I'm out of my depth here and wasn't sure what to do next. sorry

Just click "Tools >> User Agent" and select a different user agent.

---

### Post by rickyrockrat on 2012-03-11
I have this problem with Fire Fox 10.0.2, and it just started with NewEgg's new, hard-to-use interface.  When I use the advanced search or any of the other search tools, I get:
"The page you are trying to view cannot be shown because it uses an invalid or unsupported form of compression."

The work around is as follows:
1) in the address bar, type 'about:config'
2) Select 'I'll be careful, I promise' or something along those lines.
3) Filter the results by typing network.http in the filter box.
4) Right-click and select Modify the network.http.accept-encoding from it's default of 'gzip, deflate' to nothing.
5) Click OK.
6) These changes take effect immediately, so hit the try again button on the page that's giving you trouble and see if it loads.  If so, you can add back, one-by-one each of the compression methods.

You can also try the string 'gzip, deflate,compress', which seems to ALSO fix the issue.

This parameter sets the compression for FireFox. You will find that the page loads slower, since FireFox is no longer requesting and receiving compressed data.

I obtained some info from here:
[http://forums.mozillazine.org/viewtopic.php?f=5&t=467079]("http://forums.mozillazine.org/viewtopic.php?f=5&t=467079")



Cheers!

---

### Post by monstrous behaviour on 2012-03-12
> **rickyrockrat said:**
> I have this problem with Fire Fox 10.0.2, and it just started with NewEgg's new, hard-to-use interface.  When I use the advanced search or any of the other search tools, I get:
"The page you are trying to view cannot be shown because it uses an invalid or unsupported form of compression."

The work around is as follows:
1) in the address bar, type 'about:config'
2) Select 'I'll be careful, I promise' or something along those lines.
3) Filter the results by typing network.http in the filter box.
4) Right-click and select Modify the network.http.accept-encoding from it's default of 'gzip, deflate' to nothing.
5) Click OK.
6) These changes take effect immediately, so hit the try again button on the page that's giving you trouble and see if it loads.  If so, you can add back, one-by-one each of the compression methods.

You can also try the string 'gzip, deflate,compress', which seems to ALSO fix the issue.

This parameter sets the compression for FireFox. You will find that the page loads slower, since FireFox is no longer requesting and receiving compressed data.

I obtained some info from here:
[http://forums.mozillazine.org/viewtopic.php?f=5&t=467079](http://forums.mozillazine.org/viewtopic.php?f=5&t=467079)



Cheers!

hello everyone

sorry-ungrateful so and so here......the site i was using was having server issues  (but would not admit it).  They moved to another host and it was sorted.  :confused:

sorry to have not updated

---

