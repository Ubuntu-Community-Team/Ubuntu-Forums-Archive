---
title: "Want Thunderbird to function as Evolution in ubuntu"
date: 2011-07-05
forum: General Help
---

### Post by fpgdu on 2011-07-05
I'd just like to know if there's a way to get Thunderbird to be setup, or have Ubuntu be setup (whichever is more feasible) so that the little white envelope on the task bar turns green when I get a new message in one of the mail accounts I setup in Thunderbird. I'd also like to know how to get it to play a sound when I receive a new email. I already setup Thunderbird as my default mail client. I also already setup the sound to be played in Thunderbird when I receive an email as "the default sound for new mail".

Lastly, this may be pushing my luck, but, it would be great if thunderbird's calendar could function as my systems default calendar and work with all the features, such as appointment reminders.

I'd prefer not to have to install mail-notification, but I'll do it as a last resort. It makes my single panel bar cluttered and takes up additional resources on my rapidly aging system.

Thanks.

---

### Post by pqwoerituytrueiwoq on 2011-07-05
set it as the default mail client may work
personally i removed the mail icon and got mail-notification
system -> preferences -> preferred applications

---

### Post by cottfcfan on 2011-07-05
If you use Gmail you can use gm-notify in synaptic.
Set thunderbird as your preferred client, and the envelope acts like it does with evolution.
You can also set whatever sound you want for incoming Mail.

---

### Post by Dragonbite on 2011-07-05
I would love to find out how to do this too!  I'd rather not have to wait for 11.10 *if* Thunderbird becomes the default email client!

---

### Post by fpgdu on 2011-07-07
> **cottfcfan said:**
> If you use Gmail you can use gm-notify in synaptic.
Set thunderbird as your preferred client, and the envelope acts like it does with evolution.
You can also set whatever sound you want for incoming Mail.

Thanks, that worked!

And thanks to the others for their suggestions.:p

---

### Post by haqking on 2011-07-07
I love Evolution ;-)

---

### Post by wildmanne39 on 2011-07-07
Hi, is thunderbird better then evolution? I have seen a lot of threads that say it is.

---

### Post by timgood on 2011-07-07
Popper is great - integrates seamlessly with the system tray and notifies you of new email *without having to have a running instance of Thunderbird/Evolution*. Very easy to configure and you can get it from GetDeb [here]("http://www.getdeb.net/software/Popper").

Hope this helps.

---

### Post by cottfcfan on 2011-07-07
> **wildmanne39 said:**
> Hi, is thunderbird better then evolution? I have seen a lot of threads that say it is.

Its all a matter of opinion. In my opinion it is. But others may differ.

---

### Post by haqking on 2011-07-07
Better is relative...is Ubuntu better than debian etc.

I used thunderbird for a while and cant for the life of me remember what it wouldnt do whch i liked, anyways i love evolution, there is nothing it doesnt do that  need or want it to.

I connect to a 3 different IMAP webmail accounts amongst some other accounts, and everything works great with online calendars etc etc.

---

### Post by Steeperton on 2011-07-07
[https://launchpad.net/libnotify-mozilla](https://launchpad.net/libnotify-mozilla)

---

### Post by fpgdu on 2011-07-07
> **timgood said:**
> Popper is great - integrates seamlessly with the system tray and notifies you of new email *without having to have a running instance of Thunderbird/Evolution*. Very easy to configure and you can get it from GetDeb [here]("http://www.getdeb.net/software/Popper").

Hope this helps.

How do you install that?!

---

### Post by hojjat on 2011-07-07
> **Steeperton said:**
> [https://launchpad.net/libnotify-mozilla](https://launchpad.net/libnotify-mozilla)

I am using Thunderbird 5 beta (from PPA) because I want to have Lightening too. libnotify seems not to be compatible with Thunderbird 5. How can I get the mail icon on Ubuntu 11.04 to work with Thunderbird, and not evolution?

PS: Ignore it, I will ask a separate question.

---

### Post by fpgdu on 2011-07-07
> **hojjat said:**
> I am using Thunderbird 5 beta (from PPA) because I want to have Lightening too. libnotify seems not to be compatible with Thunderbird 5. How can I get the mail icon on Ubuntu 11.04 to work with Thunderbird, and not evolution?

PS: Ignore it, I will ask a separate question.

I'm wondering the same thing. I figured out how to install it, but if i click the envelope icon then click "Mail" it goes to evolution.

I have installed all 3 plugins/packages mentioned in this thread.

---

### Post by hojjat on 2011-07-07
> **fpgdu said:**
> I'm wondering the same thing. I figured out how to install it, but if i click the envelope icon then click "Mail" it goes to evolution.

I have installed all 3 plugins/packages mentioned in this thread.

Yes, the mail icon is tied to Evolution, and there seems to be no way around it. However, after you install the Unity Integration, you get another section added under the mail icon for Thunderbird. The sad part is you have to keep Thunderbird open, or that section is gone. See [http://ubuntuforums.org/showthread.php?t=1799465](http://ubuntuforums.org/showthread.php?t=1799465)

---

### Post by timgood on 2011-07-07
> **fpgdu said:**
> How do you install that?!

Install the GetDeb repository package - you can get it from [here]("http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb"). Then go back to the Popper page and click on 'Install this now'.

Have Fun!

---

### Post by cottfcfan on 2011-07-08
What I wrote in post 3 will set the envelope icon to Thunderbird.

---

### Post by Dragonbite on 2011-07-08
I think they approved Thunderbird to replace Evolution in 11.10.  I will assume all this notifications stuff will be installed and configured out-of-the-box then!

---

### Post by timgood on 2011-07-08
> **Dragonbite said:**
> I think they approved Thunderbird to replace Evolution in 11.10.  I will assume all this notifications stuff will be installed and configured out-of-the-box then!

The problem with 'all the notification stuff' at the moment, is that in order to be notified of new mail you need to have a running instance of your mail client (Thunderbird, Evolution etc.) which can hog resources. This isn't going to change in 11.10 as far as I know. What I like about Popper is that it uses the notification tray to let you know of new messages even if your mail client is closed. The envelope turns green and, when clicked on, will open the mail client of your choice. Great bit of software!

---

### Post by Dragonbite on 2011-07-08
> **timgood said:**
> The problem with 'all the notification stuff' at the moment, is that in order to be notified of new mail you need to have a running instance of your mail client (Thunderbird, Evolution etc.) which can hog resources. This isn't going to change in 11.10 as far as I know. What I like about Popper is that it uses the notification tray to let you know of new messages even if your mail client is closed. The envelope turns green and, when clicked on, will open the mail client of your choice. Great bit of software!

The GUI client may be closed, but you still need to poll either the client's in-box or have it poll the actual account. Not sure if IMAP would cause additional issues, either.

---

### Post by timgood on 2011-07-08
> **Dragonbite said:**
> The GUI client may be closed, but you still need to poll either the client's in-box or have it poll the actual account. Not sure if IMAP would cause additional issues, either.

From the Popper home page: "Popper reads the new emails from POP3 and IMAP email servers and notifies about the number, subject, sender and time of new emails in the indicator applet and via a notification bubble."

---

### Post by Dragonbite on 2011-07-08
> **timgood said:**
> From the Popper home page: "Popper reads the new emails from POP3 and IMAP email servers and notifies about the number, subject, sender and time of new emails in the indicator applet and via a notification bubble."

So it polls the service and retrieves only the header information.  makes sense.

---

### Post by hojjat on 2011-07-10
> **cottfcfan said:**
> What I wrote in post 3 will set the envelope icon to Thunderbird.

You said "Set thunderbird as your preferred client, and the envelope acts like it does with evolution." I did that but it didn't help.

---

### Post by hojjat on 2011-07-10
> **timgood said:**
> The problem with 'all the notification stuff' at the moment, is that in order to be notified of new mail you need to have a running instance of your mail client (Thunderbird, Evolution etc.) which can hog resources. This isn't going to change in 11.10 as far as I know.

In 11.04, Evolution does this using a resident process called evolution-alarm-notify. I assume in 11.10 we will have a similar resident process called thunderbird-alarm-notify or alike. The indicator-messages-services hooks to that process and notifies you when a new mail is received.

---

### Post by cottfcfan on 2011-07-10
hojjat.
It works fine for me.
Open up gmail notifier configuration, fill in the details, tick the box "current default mail client" in Account, and autostart in Enhanced. Play a sound also if you want.
Now whenever you have incoming Mail, the Envelope icon turns green, and a sound plays. Just click the Envelope and "Inbox", and Thunderbird automatically opens instead of Evolution.

---

### Post by timgood on 2011-07-10
> **hojjat said:**
> In 11.04, Evolution does this using a resident process called evolution-alarm-notify. I assume in 11.10 we will have a similar resident process called thunderbird-alarm-notify or alike. The indicator-messages-services hooks to that process and notifies you when a new mail is received.

Hmmn. Yes the point I'm making is that in order for this to happen, you need to have a *running* instance of either Evolution or Thunderbird. With Popper, you don't. It will notify you of emails if neither process is running, because it polls the server (either POP or IMAP). This is less resource hungry.

---

### Post by hojjat on 2011-07-11
> **cottfcfan said:**
> hojjat.
It works fine for me.
Open up gmail notifier configuration, fill in the details, tick the box "current default mail client" in Account, and autostart in Enhanced. Play a sound also if you want.
Now whenever you have incoming Mail, the Envelope icon turns green, and a sound plays. Just click the Envelope and "Inbox", and Thunderbird automatically opens instead of Evolution.

Oh, I thought the second statement is independent of the first. Does your method work for non-Gmail accounts too? And does it support multiple accounts?

---

### Post by hojjat on 2011-07-11
> **timgood said:**
> Hmmn. Yes the point I'm making is that in order for this to happen, you need to have a *running* instance of either Evolution or Thunderbird. With Popper, you don't. It will notify you of emails if neither process is running, because it polls the server (either POP or IMAP). This is less resource hungry.

And what I'm trying to say is that you don't have to have an instance of Evolution or Thunderbird open. A separate process (in the case of Ubuntu 11.04, evolution-alarm-notify) handles that part and opens the mail client when you click on the mail icon, etc. That process, much like Popper, is much less resource hungry.

In other words, evolution-alarm-notify is the Popper of Ubuntu 11.04, but it's better since it integrates with the mail icon. A similar process is expected to exist in 11.10 which integrates with mail icon and calls Thunderbird.

---

### Post by Dragonbite on 2011-07-11
Is there any benefit with the notification already pulling down headers, when you go into Thunderbird client application and it pulls down those headers again (or can it use what was downloaded and notified already)?

---

### Post by timgood on 2011-07-11
> **hojjat said:**
> And what I'm trying to say is that you don't have to have an instance of Evolution or Thunderbird open. A separate process (in the case of Ubuntu 11.04, evolution-alarm-notify) handles that part and opens the mail client when you click on the mail icon, etc. That process, much like Popper, is much less resource hungry.

In other words, evolution-alarm-notify is the Popper of Ubuntu 11.04, but it's better since it integrates with the mail icon. A similar process is expected to exist in 11.10 which integrates with mail icon and calls Thunderbird.

Ahh, it all makes sense now. I didn't know that this feature was now part of 11.04! Popper does integrate with the mail icon.

---

### Post by timgood on 2011-07-11
@hojjat

Are you sure that this works in Natty? It doesn't on my 11.04 machine. I have to have Evolution running in order to get notifications. If Evolution is closed, I get nothing.

I have ticked the box in mail preferences to be notified of new mail. However, nothing happens with Evolution closed.

---

### Post by hojjat on 2011-07-12
> **timgood said:**
> @hojjat

Are you sure that this works in Natty? It doesn't on my 11.04 machine. I have to have Evolution running in order to get notifications. If Evolution is closed, I get nothing.

I have ticked the box in mail preferences to be notified of new mail. However, nothing happens with Evolution closed.

I didn't try it in 11.04 because I simply couldn't get Evolution to work the way I wanted it.

---

### Post by timgood on 2011-07-12
> **hojjat said:**
> I didn't try it in 11.04 because I simply couldn't get Evolution to work the way I wanted it.

OK. Has anyone managed to get notifications working without a running instance of Evolution? I've also been looking online for documentation of this feature, but I can't seem to find it.

---

### Post by timgood on 2011-07-15
I'll take that as a 'no' then.

---

### Post by wildmanne39 on 2011-07-31
Hi, I just installed gm-notify and it works great in natty with gmail, and thundrbird does not have to be open.

---

### Post by surfer on 2011-08-16
> **timgood said:**
> OK. Has anyone managed to get notifications working without a running instance of Evolution? I've also been looking online for documentation of this feature, but I can't seem to find it.

i just installed popper and it works without a running evolution.
```
$ ps -u my_username | grep evolution
``` returned nothing but popper notified me about new mails.

you can also check whether or not poppler is running with
```
tail -f /home/my_username/.popper/popper.log
```

---

