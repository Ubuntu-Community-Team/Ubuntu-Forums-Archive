---
title: "logmein Alternative?"
date: 2009-07-30
forum: General Help
---

### Post by wpwend42 on 2009-07-30
Here is my situation: My parents run XP still and need me to go in to their computer occasionally.  I like to do regular maintenance also so they don't have to be bothered with it.  On Windows, I always used logmein to do this.  That program doesn't work so well in Ubuntu it seems.

So my question is, what is the best way to connect between my Ubuntu laptop and their XP computer?  Thanks.

---

### Post by zzzBrett on 2009-07-30
> **wpwend42 said:**
> Here is my situation: My parents run XP still and need me to go in to their computer occasionally.  I like to do regular maintenance also so they don't have to be bothered with it.  On Windows, I always used logmein to do this.  That program doesn't work so well in Ubuntu it seems.

So my question is, what is the best way to connect between my Ubuntu laptop and their XP computer?  Thanks.

The easiest would probably be running a VNC server from your parents computer.  Ubuntu comes with a VNC client.

There are plenty of VNC servers you can set up for them.

I've used and had no problems with both RealVNC and TightVNC

---

### Post by zzzBrett on 2009-07-30
You could also try Remote Help Assistant.  I've been wanting to test it out but haven't gotten around to it.

[http://pileofstuff.org/remote-help-assistant/](http://pileofstuff.org/remote-help-assistant/)

Edit: Nevermind - doesn't work for windows.

---

### Post by rbc on 2009-07-30
The logmein software is installed on the XP computer, so you can still use logmein from Ubuntu, since your end of end is simply a matter of logging in via logmein's web page

---

### Post by zzzBrett on 2009-07-30
> **rbc said:**
> The logmein software is installed on the XP computer, so you can still use logmein from Ubuntu, since your end of end is simply a matter of logging in via logmein's web page

Logmein relies mostly on activex.  Without activex, they have a very basic interface, which I assume the OP has already experienced (and wanted more).

---

### Post by wpwend42 on 2009-07-31
Yeah on the Ubuntu end logmein gives me their desktop but I cannot click on anything or generally do anything.  I'll try out the VNC suggestion.

---

### Post by rbc on 2009-07-31
I'm really truly not trying to push logmein on you. I have used VNC and rather enjoy it. The issues I had with Ubuntu and logmein never had anything to do with activeX. It was almost always because of Ubuntu and some Java conflict. This may or may not help, but it is worth a look if you want to try and keep logmein as an option:
[https://secure.logmein.com/labs.asp](https://secure.logmein.com/labs.asp)

---

### Post by hibliss on 2009-07-31
You can also RDP to the Windows box from Ubuntu remotely.

---

### Post by zzzBrett on 2009-07-31
> **rbc said:**
> I'm really truly not trying to push logmein on you. I have used VNC and rather enjoy it. The issues I had with Ubuntu and logmein never had anything to do with activeX. It was almost always because of Ubuntu and some Java conflict. This may or may not help, but it is worth a look if you want to try and keep logmein as an option:
[https://secure.logmein.com/labs.asp](https://secure.logmein.com/labs.asp)

I didn't know about this -- thanks.

---

### Post by rbc on 2009-07-31
> I didn't know about this -- thanks. 
I have been using Ubuntu since 7.04. Initially I had problems because logmein didn't like Java 6. I installed and used Java 5 and was fine until a week or so again, until some updates messes things up again. I wish I could give credit where credit is due, but someone here suggested that link, and all has been well since

---

### Post by rbc on 2009-07-31
Oh, and if anyone from logmein is listening, thanks for supporting linux

---

### Post by wpwend42 on 2009-08-02
That Firefox plugin worked for me!  Thanks.

---

