---
title: "ff on wine?"
date: 2009-09-11
forum: General Help
---

### Post by xdweaver on 2009-09-11
how to properly setup FF via Wine with the flash on it. i am new and have no idea how to do that.

---

### Post by P4man on 2009-09-11
Why would you want to run firefox on wine when there is native firefox and flash?

---

### Post by akakingess on 2009-09-11
You should not need to use wine for Firefox (if that is what you mean when you say FF), it is actually in the Synaptic Package Manager and 100% supported native within Ubuntu and there are ways to get Flash and other plugins working fine as well, although you may want to search the forums for your best option since there are more than 1 way to do so.

---

### Post by xdweaver on 2009-09-11
my daughter is killing me. I put ubuntu on her pc. and now she can not go to the buildabearville site. when she tries to log on it just goes back to the login screen. I have installed flash and still nothing. So I thought that ff on wine would be a good fix.. any ideas on that. thanks for suck a fast reply. daniel

---

### Post by P4man on 2009-09-11
its should work with the native firefox and flash.
Make sure you have the right flash plugin installed. Go to system > administration > synaptic package manager. Search for "flash". Right click on "adobe-flashplugin" and mark for install. Check if you have any other flash plugins installed like gnash, and mark them for removal. Click apply. Close and restart firefox. Should work.

---

### Post by akakingess on 2009-09-11
Just so you know why I am not responding quickly, I choose not to use wine at all, try to keep Ubuntu 100% Ubuntu, sorry I can't help, but I have 3 kids and they use both our windows machines and Ubuntu machines for sites such as clubpenguin.com, and webkinz, and I have seen no problem and they see no difference.

---

### Post by lovinglinux on 2009-09-11
Also check the Flash Optimization section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by davidryderuk on 2009-09-11
Hi,
Just an idea but maybe you should try the following firefox extension.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

The general idea is that when your website asks the browser for its ID then it reports it's internet explorer even if it's not. 

Basically what you have to do is the following:

1. Visit the link above and install User Agent Switcher.

2. Restart firefox.

3. Select the option Tools > Default User Agent > Internet Explorer > Internet Explorer 8

4. Then visit your website again. This won't solve any problems with flash, but it should stop you being banned from the website just because your not using windows.

---

### Post by P4man on 2009-09-11
> **davidryderuk said:**
> Hi,
Just an idea but maybe you should try the following firefox extension.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)


Id only do that when all else fails. Lets not keep the myth alive that everyone uses IE :) The site the OP mentioned seems to work just fine with my FF and flash (though Im using FF 3.5.2)

---

### Post by davidryderuk on 2009-09-11
Did you actually log into the website though? In any case there is a similar thread available below which has more people suffering from the same problem.

[http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&comments_parentId=385192&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&comments_parentId=385192&forumId=1)

A particularly interesting point is the website error someone quotes as being:

> Webpage error details
User Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.1; Trident/4.0; GTB6; .NET CLR 2.0.50727; .NET CLR 3.0.4506.2152; .NET CLR 3.5.30729) 

---

### Post by XCan on 2009-09-11
Firefox should work excellent with Wine [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1930](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1930) . The unfortunate fact can also be added that FF is actually faster through Wine than the native client (dunno if that got changed with 3.5).

---

### Post by BUSHYBOB on 2009-09-11
When I tried to access [http://www.buildabearville.com/](http://www.buildabearville.com/) I get this error.
Hardy and firefox  3.5.1pre 



Content Encoding Error    

          

The page you are trying to view cannot be shown because it uses an invalid or unsupported form of compression.

---

### Post by oboedad55 on 2009-09-11
> **BUSHYBOB said:**
> When I tried to access [http://www.buildabearville.com/](http://www.buildabearville.com/) I get this error.
Hardy and firefox  3.5.1pre 



Content Encoding Error    

          

The page you are trying to view cannot be shown because it uses an invalid or unsupported form of compression.

I got this same error on Jaunty with FF 3.0.13. Then I went back and have no problem. Wait... I have updated to .14 in between. That shouldn't make any difference, but perhaps?

---

### Post by BUSHYBOB on 2009-09-11
No error with 3.0.11 on that page, but same login problem.

---

### Post by joshzam on 2009-09-11
It very nice that people are trying to get buildabearville to work, but can anyone actually help with the original question? If someone wants to install FF via Wine then that is their prerogative. How does one then install the Flash plugin successfully?

I'm stuck with the same problem - not for buildabearville purposes, though. :) FF installs and runs perfectly via Wine but once Flash is needed - like on Youube - the automatic "Get the latest Flash player" process does not seem to work for me. It installs, restarts FF, and then throws up this error:

getPlus+(R): Error
Operating system error! (16244.202.235-43772312.80040152.FFFFFFFF.80004002)

Any ideas?

---

### Post by oboedad55 on 2009-09-11
> **joshzam said:**
> It very nice that people are trying to get buildabearville to work, but can anyone actually help with the original question? If someone wants to install FF via Wine then that is their prerogative. How does one then install the Flash plugin successfully?

I'm stuck with the same problem - not for buildabearville purposes, though. :) FF installs and runs perfectly via Wine but once Flash is needed - like on Youube - the automatic "Get the latest Flash player" process does not seem to work for me. It installs, restarts FF, and then throws up this error:

getPlus+(R): Error
Operating system error! (16244.202.235-43772312.80040152.FFFFFFFF.80004002)

Any ideas?

Do a search on this site: [http://www.winehq.org/](http://www.winehq.org/)

---

