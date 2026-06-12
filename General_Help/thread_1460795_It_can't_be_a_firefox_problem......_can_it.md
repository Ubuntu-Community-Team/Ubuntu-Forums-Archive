---
title: "It can't be a firefox problem...... can it"
date: 2010-04-23
forum: General Help
---

### Post by whitefeather010 on 2010-04-23
Ok here's my problem.  Firefox keeps freezing.  the process keeps running.  I've uninstalled firefox, installed different versions, ie 3.6, 3.7 etc, I've removed my profile folder in my home directory.  same results.  I've ran firefox as a SU and I get this output from the terminal

(firefox-bin:28892): GLib-WARNING **: g_set_prgname() called multiple times
/home/josh/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
  (parent won, so we're not deferring)
  (parent won, so we're deferring)
  (processing deferred in-call)
  (child won, so we're not deferring)
  (child won, so we're deferring)
  (processing deferred in-call)
NOTE: child process received `Goodbye', closing down


any ideas?

---

### Post by ellgor on 2010-04-23
Hi,

Suggestion, install "Galeon" its based on the gecko engine same as FF, is a lot smaller and in the year Ive used it, never crashed once.

Regards, Ellgor.

---

### Post by lovinglinux on 2010-04-23
> **whitefeather010 said:**
> Ok here's my problem.  Firefox keeps freezing.  the process keeps running.  I've uninstalled firefox, installed different versions, ie 3.6, 3.7 etc, I've removed my profile folder in my home directory.  same results.  I've ran firefox as a SU and I get this output from the terminal

(firefox-bin:28892): GLib-WARNING **: g_set_prgname() called multiple times
/home/josh/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
  (parent won, so we're not deferring)
  (parent won, so we're deferring)
  (processing deferred in-call)
  (child won, so we're not deferring)
  (child won, so we're deferring)
  (processing deferred in-call)
NOTE: child process received `Goodbye', closing down


any ideas?

You shouldn't run Firefox with sudo. Doing that, you have lost the ownership of ~/.mozilla folder, which causes lots of problems, including preventing the browser to start. [See this to fix it](http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2).

What version of Ubuntu you are running? Does it crash at start, on any page or specific pages?

See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by jjossarin on 2010-05-24
> **ellgor said:**
> Hi,

Suggestion, install "Galeon" its based on the gecko engine same as FF, is a lot smaller and in the year Ive used it, never crashed once.

Regards, Ellgor.

I installed and used it. Crashed three times in a row with just 5 tabs.
Galeon hasn't been under active development since 2005 and it looks Epiphany is the one that replaced galeon. A few years back, I used to use Epiphany a lot- but I think Firefox is a lot better, especially in newer versions.

> **whitefeather010 said:**
> Ok here's my problem.  Firefox keeps freezing.  the process keeps running.  I've uninstalled firefox, installed different versions, ie 3.6, 3.7 etc, I've removed my profile folder in my home directory.  same results.  I've ran firefox as a SU and I get this output from the terminal

(firefox-bin:28892): GLib-WARNING **: g_set_prgname() called multiple times
/home/josh/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
  (parent won, so we're not deferring)
  (parent won, so we're deferring)
  (processing deferred in-call)
  (child won, so we're not deferring)
  (child won, so we're deferring)
  (processing deferred in-call)
NOTE: child process received `Goodbye', closing down


any ideas?

I am facing the exactly same problem. Firefox runs ok for sometime, then as the number of tabs or the duration of use (any of them) increases, then the CPU fan sound increases, firefox response-time decreases, all other OS responses also become slower. And exactly the same message is displayed in the terminal. When I close Firefox from the File->Quit menu, these messages persist, and firefox-bin is shown in the process list. I have to forcefully kill the process from the terminal. I have submitted numerous crash reports. I have tried numerous versions of Firefox, including the pre-release versions. Each newer version behaves better, but all of them freeze. I haven't tested the messages in terminal for earlier versions, but 3.7a3pre gives the messages quoted above.

> **lovinglinux said:**
> You shouldn't run Firefox with sudo. Doing that, you have lost the ownership of ~/.mozilla folder, which causes lots of problems, including preventing the browser to start. [See this to fix it]("http://lovinglinux.megabyet.net/?page_id=220#Firefox-doesn%27t-start-through-regular-command/menu-but-starts-using-%22sudo-firefox%22--2").

What version of Ubuntu you are running? Does it crash at start, on any page or specific pages?

See [[COLOR=Sienna]**General Troubleshooting Steps**[/COLOR]]("http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2") section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").

I don't fireup Firefox using SUDO. And the links you provided have no mention of the problems the original poster mentions of. They are useful in other ways though, thanks for that.

Thanks.

---

### Post by jjossarin on 2010-05-24
[I](<unknown>:13577): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

  (child won, so we're deferring)[/I] [I]
  (child won, so we're not deferring)
  (processing deferred in-call)[/I]



I thought this additional information help. Even while Firefox is running alright (just opened, only a few tabs), the messages given above appear in the terminal. When the duration of use or number of tabs increase (more than 70-80 tabs or more than 6-7 hours), then only the following messages appear, without the message starting with [B](<unknown>:13577) or (<unknown>:16267)



[/B]  [I](child won, so we're not deferring)
  (processing deferred in-call)
[/I]

After quitting Firefox from File menu, the following error messages appear (many in number):

[I]
Killed

###!!! [Child][RPCChannel] Error: Channel error: cannot send/recv[/I]  


Any help or pointers to further help will be highly appreciated.

---

### Post by lovinglinux on 2010-05-24
> **jjossarin said:**
> I don't fireup Firefox using SUDO. And the links you provided have no mention of the problems the original poster mentions of. They are useful in other ways though, thanks for that.

The OP did started Firefox with sudo and the link I provided helps to fix the issues created by that action, which is necessary before troubleshooting the original problem.

---

### Post by jjossarin on 2010-05-25
> **lovinglinux said:**
> The OP did started Firefox with sudo and the link I provided helps to fix the issues created by that action, which is necessary before troubleshooting the original problem.

Oops- yes you're right. I am sorry for not realizing that.

Any idea about why this problem happens even without "sudo" ?

Thanks.

---

### Post by lovinglinux on 2010-05-25
> **jjossarin said:**
> Oops- yes you're right. I am sorry for not realizing that.

Any idea about why this problem happens even without "sudo" ?

Thanks.


Could be problematic extension or plugin, a corrupted profile, a corrupted Firefox installation or even some Gnome settings.

---

### Post by jjossarin on 2010-05-25
> **lovinglinux said:**
> Could be problematic extension or plugin, a corrupted profile, a corrupted Firefox installation or even some Gnome settings.

For the sake of testing, I am using Firefox without any extensions. I create a new profile almost every week and use it. I think it might be one of problematic plugin or GNOME settings.

What more information can I provide that would help in diagnosing this problem?

Thanks

---

### Post by lovinglinux on 2010-05-25
> **jjossarin said:**
> For the sake of testing, I am using Firefox without any extensions. I create a new profile almost every week and use it. I think it might be one of problematic plugin or GNOME settings.

What more information can I provide that would help in diagnosing this problem?

Thanks

I would suggest creating a new thread for your problem. Although the OP has been quite, is not very good to hijack a thread.

If creating a new profile doesn't help, then I would create a new Ubuntu user and login with that account to see if the problem persists. This new user will have clean Gnome default settings.

---

### Post by r0t on 2010-11-01
I have the same problem, for every user, and for every FF / Swiftfox installation on my Ubuntu Netbook edition 10.10. No plugins / extensions. Creating a new FF profiles sometimes seem to solve the problem for a few sessions. Any news on this?

---

