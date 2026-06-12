---
title: "Google Voice"
date: 2012-09-14
forum: General Help
---

### Post by ddjolley on 2012-09-14
I need some help deciding how Ubuntu can best help me use Google Voice.

I keep open a browser instance in which I am logged into gmail so that I can answer incoming calls.  When a call comes in I have to scramble to find that instance and bring it into focus so that I can answer the call.  What would be absolutely great would be to have a pop-up appear that would allow me to answer the call.  That's probably asking a bit much.  I attended an Ubuntu meeting recently in which a new feature of 12.10 was mentioned which sounded like it might help me with this problem.  I don't really remember any of the specifics about the feature.

Anyway, what I'm looking for is suggestions on how I can best handle this problem both immediately and after 12.10 is released (if there is any difference).  TIA for any input.

       ... doug

---

### Post by wojox on 2012-09-14
You want to trigger the NotifyOSD. Open a terminal Ctrl+Alt+T:
```
notify-send Google ring
```

---

### Post by ddjolley on 2012-09-15
> notify-send Google ring

Entering, "notify-send Google ring" at the command prompt causes the bubble to appear with "Google" on the first line and "ring" on the second.  So, I'm going to hazard that it works.

I truly hate to be so dense; but, I don't see how that helps me.  I called my GV number from another line and nothing happened on my Ubuntu desktop.  I'm absolutely confident that what you have given me is exactly what I'm looking for.  Apparently, I just don't have the smarts to appreciate how it works.  Could you please help me a bit more and provide some guidance on how this is going to help me?  Sorry.  Thanks.

      ... doug

---

### Post by jones27557 on 2012-09-15
Me too.   That would be cool.

---

### Post by blueshead on 2012-09-15
There are apps for Windows, You can do this in growl in OSX.

But the closet I could find for Linux is this.. [http://googsystray.sourceforge.net/]("http://googsystray.sourceforge.net/")

I don't know how to compile.. Maybe someone can show us how?

I'd love a system wide pop up when I get a GV call. I did make my gmail page into a webapp using fogger so I don't have to keep GV open in a browser tab. 

Works fine.. I just park it in a workspace.. Howsoever.. If I'm gaming or playing music.. I won't hear an incoming call ring.. A system pop up notifier would be great!    :idea:

---

### Post by newb85 on 2012-09-15
Er...Wojox was only making the point that you might want to use the system notifications.  That command was only an example of how those notifications are called.  You would need to work it into a bash script that monitors Google Voice and then issues the notify-send command when there is an incoming call.

---

### Post by newb85 on 2012-09-15
I think I've found what you're looking for.  It's a couple years old, and the project doesn't seem to have ongoing support, but I successfully installed it on a VM with Precise.  It integrates into the menu as it should, and clicking on it brings up a prompt for Google Voice credentials.  Unfortunately, I'm not set up with Google Voice yet, so I can't test it any further than that.

Read more [here]("http://www.omgubuntu.co.uk/2010/06/add-google-voice-alerts-to-the-ubuntu-messaging-menu").

---

### Post by newb85 on 2012-09-15
I was wrong.  While my previous post is a great way to easily check for voicemails and SMS, I don't think it does anything for incoming calls.

---

### Post by blueshead on 2012-09-15
I found a deb package for it.. It installs.. but crashes at points. Also after setting it up for GV and calling the number.. I get no pop up.. o well.

[http://linux.softpedia.com/progDownload/googsystray-Download-50805.html]("http://linux.softpedia.com/progDownload/googsystray-Download-50805.html")

---

### Post by blueshead on 2012-09-15
> **newb85 said:**
> I think I've found what you're looking for.  It's a couple years old, and the project doesn't seem to have ongoing support, but I successfully installed it on a VM with Precise.  It integrates into the menu as it should, and clicking on it brings up a prompt for Google Voice credentials.  Unfortunately, I'm not set up with Google Voice yet, so I can't test it any further than that.

Read more [here]("http://www.omgubuntu.co.uk/2010/06/add-google-voice-alerts-to-the-ubuntu-messaging-menu").

newb85.. This is almost what we need. It's very good and it does do a pop up message... When I set it up I checked it for 1 minute. After set up..I can find no way to go back in to edit it.

At least at 1 minute.. I can get to the voice message fast and return the call. I'm wondering if there is a way to edit it..to say 10-15 seconds and I might be able to answer the call. Still , this is getting close.. :)

---

### Post by newb85 on 2012-09-15
> **blueshead said:**
> I found a deb package for it.. It installs.. but crashes at points. Also after setting it up for GV and calling the number.. I get no pop up.. o well.

[http://linux.softpedia.com/progDownload/googsystray-Download-50805.html]("http://linux.softpedia.com/progDownload/googsystray-Download-50805.html")

Why did you download the *.deb, rather than adding the developer's ppa, as described in the article I linked?

---

### Post by ddjolley on 2012-09-15
Wow!!  Thanks for all the input.

Having read the responses, I think that I need to clarify a bit. I'm not particularly concerned about notification per se.  While a pop-up on-screen notification would be nice frosting on the cake, the audible notification alone is a quite satisfactory means of notification as far as I am concerned.  Now, if the pop-up included an element to click-on so that the incoming call could be ANSWERED, that would be something else.  That's because it is the actual *ANSWERING* of the incoming call that concerns me.  That is to say, when I receive notice of an incoming call (by whatever means) I now need to hunt around and find the open browser instance that's running gmail, bring it into focus, and finally I get to answer the incoming call.  I'm looking for a way to simplify the process of ANSWERING the incoming call.  Suggestions?  Thanks for any input.

         ... doug

---

### Post by newb85 on 2012-09-15
> **blueshead said:**
> newb85.. This is almost what we need. It's very good and it does do a pop up message... When I set it up I checked it for 1 minute. After set up..I can find no way to go back in to edit it.

At least at 1 minute.. I can get to the voice message fast and return the call. I'm wondering if there is a way to edit it..to say 10-15 seconds and I might be able to answer the call. Still , this is getting close.. :)

If you want to re-enter the settings,

```
$ gvoice-notifier --help
```

will do the trick.  Note, however, that it will only take integer minute values.  If you enter 0 minutes, your notifications will be instantaneous.  Even then, however, it will not notify you of calls.  I think this notifier was only designed to let you know about voicemails and texts.

---

### Post by newb85 on 2012-09-15
> **ddjolley said:**
> Wow!!  Thanks for all the input.

Having read the responses, I think that I need to clarify a bit. I'm not particularly concerned about notification per se.  While a pop-up on-screen notification would be nice frosting on the cake, the audible notification alone is a quite satisfactory means of notification as far as I am concerned.  Now, if the pop-up included an element to click-on so that the incoming call could be ANSWERED, that would be something else.  That's because it is the actual *ANSWERING* of the incoming call that concerns me.  That is to say, when I receive notice of an incoming call (by whatever means) I now need to hunt around and find the open browser instance that's running gmail, bring it into focus, and finally I get to answer the incoming call.  I'm looking for a way to simplify the process of ANSWERING the incoming call.  Suggestions?  Thanks for any input.

         ... doug

I don't know that it's possible to have a browser jump to the forefront when your call is incoming.  I think ideally, there would be a client you could use instead of the browser.  However, I'm not aware of any such client.

---

### Post by blueshead on 2012-09-15
> **newb85 said:**
> Why did you download the *.deb, rather than adding the developer's ppa, as described in the article I linked?

the .deb is for another app, not the one you suggested.

I installed your suggestion via ppa. I now wish to edit it.

---

### Post by markbl on 2012-09-15
OP, IMHO the best way to deal with this is to install the [Chat for Google](https://chrome.google.com/webstore/detail/chat-for-google/nckgahadagoaajjgafhacjanaoiihapd) chrome extension by google. That extension runs in the browser but runs like a background app, i.e. just like skype etc so you don't even need a chrome window open anywhere. When you click on it it opens a small contacts window from your systray, or incoming chats/talk/hangouts will open from there. Amazingly, at at least on Max OSX where I use it also, it even integrates a task icon into the systray. I think it is the best way to integrate google chat + talk + hangouts. I don't understand why Google don't integrate that extension formally into chrome.

---

### Post by blueshead on 2012-09-15
> **markbl said:**
> OP, IMHO the best way to deal with this is to install the [Chat for Google](https://chrome.google.com/webstore/detail/chat-for-google/nckgahadagoaajjgafhacjanaoiihapd) chrome extension by google. That extension runs in the browser but runs like a background app, i.e. just like skype etc so you don't even need a chrome window open anywhere. When you click on it it opens a small contacts window from your systray, or incoming chats/talk/hangouts will open from there. Amazingly, at at least on Max OSX where I use it also, it even integrates a task icon into the systray. I think it is the best way to integrate google chat + talk + hangouts. I don't understand why Google don't integrate that extension formally into chrome.


This works perfect!  Thank you.. It popped up as soon as the first ring.. Plenty of time to answer the phone.. Will you have my children?  

The nice thing is after opening it in google browser..you cab shut the browser down and it acts like a stand alone app.;)

---

### Post by ddjolley on 2012-09-16
Again I hate to be the dense one in the crowd.

I installed the Chat for Google extension into Chrome.  The browser icon is present and when I hover over it, it says that the status is connected.  I have yet to see an icon in the system tray although all of the options boxes are checked in the configuration.  I have actually seen the pop-up appear in response to an incoming call.  When it works, it's real nice.  However, at the moment, it doesn't seem to be working (i.e., no pop-up in response to incoming calls).  Any thoughts on how I can get the icon into the system tray and get more reliable operation?  BTW, I'm running Ubuntu 12.04.  Thanks.

     ... doug

---

### Post by markbl on 2012-09-16
@ddjolley I don't think the systray icon appears in Unity or Gnome Shell. As I said above the tray icon appears for me at least on Mac OSX. Other than that, chats and incoming hangout calls work fine for me using Gnome Shell on Ubuntu 12.04 most of my day. Perhaps you have network/internet issues?

---

### Post by ddjolley on 2012-09-16
Thanks for the clarification. I didn't understand that the systray icon thing might not work and I was viewing the fact that it didn't as an indication of trouble.  Consequently, I never did really get much beyond that point in my trouble shooting efforts.  I installed some updates (Chat for Google was affected) and now I seem to have things working without the systray icon.

Things seem to be working fine in terms of delivering a pop-up from which an incoming call can be answered even WITHOUT a single instance of Chrome running.  That alone goes well beyond my initial wish list.  However, I do think not having the systray icon sort of makes me a 2nd class citizen WRT Chat for Google :-)  The reason I say that is that with the systray icon I suspect that I would be able to place outgoing calls as well without a single instance of Chrome running.  That's a pretty big plus.

Initially I thought that I might be able to send text messages from Chat for Google.  I don't think that's the case whether or not the systray icon is available.  That would have been very nice too; but, obviously goes way beyond my initial wish list.

I think my problems are solved.  (After all, I got everything on my wish list and more.)  Let me think about it over night.  Unless I come up with something additional, I'll mark the thread solved tomorrow.  Thanks for your input.  You have been a very big help.

       ... doug

---

### Post by ddjolley on 2012-09-17
In reflecting on this issue, I'm wondering if it would not be appropriate for us to understand WHY the systray icon feature doesn't work in Ubuntu.  For example, here's a link ( [http://blog.jvc26.org/2011/09/15/fixing-ubuntu-natty-tray](http://blog.jvc26.org/2011/09/15/fixing-ubuntu-natty-tray) ) that suggests that applications need to be white listed in order to appear in the systray.  There may be other similar issues.  If the problem is a bug somewhere, maybe it should be fixed.  The point is that the systray icon seems to be an extremely valuable feature.  IMHO, it shouldn't just be dismissed.  FWIW.

       ... doug

---

