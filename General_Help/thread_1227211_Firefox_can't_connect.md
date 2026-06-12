---
title: "Firefox can't connect"
date: 2009-07-30
forum: General Help
---

### Post by swiftwood on 2009-07-30
I fired up the Linux box last night.

When I tried Firefox I got a message about an add-on compatibility check

After it finish, which took a while, Firefox can no longer get to outside sites.

The lights on the router don't light up.


I updated it two days ago, and it worked fine.

---

### Post by DeMus on 2009-07-30
> **swiftwood said:**
> I fired up the Linux box last night.

When I tried Firefox I got a message about an add-on compatibility check

After it finish, which took a while, Firefox can no longer get to outside sites.

The lights on the router don't light up.


I updated it two days ago, and it worked fine.

Does your e-mail or chat-program still work? In other words, in your computer still connected to the net?

---

### Post by TeoBigusGeekus on 2009-07-30
Have you tried with another browser? (Opera, Epiphany, etc.)

---

### Post by swiftwood on 2009-07-30
Firefox is the only browser I use

I don't use mail or chat rooms

Should I be able to ping other sites?

What I don't get is that I was in a 'user' account, w/o install privileges.

Should I just turn the add-ins off an see if that does it?

---

### Post by DeMus on 2009-07-30
> **swiftwood said:**
> Firefox is the only browser I use

I don't use mail or chat rooms

Should I be able to ping other sites?

What I don't get is that I was in a 'user' account, w/o install privileges.

Should I just turn the add-ins off an see if that does it?

Yes, try to ping in a terminal, for example: ping [www.cnn.com](www.cnn.com)
See what is the answer.
I that works, start firefox in a terminal also using
firefox --safe-mode
It will start without the add-ons. See if that works for you. If it does, enable the add-ons one by one to see which is the bad guy.

---

### Post by swiftwood on 2009-07-30
Thanks I'll try that.

The linux box it @ home.

BTW I forget how to setup my display:0.O so I can run gui interfaces.

How's that go again?

---

### Post by lovinglinux on 2009-07-30
See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

### Post by swiftwood on 2009-07-30
It WASN"T Firefox


I couldn't ping [www.cnn.com](www.cnn.com)

I could ping my router

So I decided to check the Update Manager, which not only could see out, but saw additional updates

Once they were loaded, I was fine!

I'm back up and running!

Thanks!

---

