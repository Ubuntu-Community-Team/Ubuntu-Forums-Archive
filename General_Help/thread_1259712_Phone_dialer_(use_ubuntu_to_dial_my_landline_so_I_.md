---
title: "Phone dialer (use ubuntu to dial my landline so I may speak over landlines)"
date: 2009-09-06
forum: General Help
---

### Post by fisheater on 2009-09-06
Phone dialer (use ubuntu to dial my landline so I may speak over landlines)

Hi all,

Searching for this was not much help.

Problem: I use calling cards for long distance calls. These require entering long strings of numbers and pauses in the form of commas. In XP I used dialer.exe to dial, then would pick up the landline phone and speak over the landline.

(for eg. See: [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/dialer_whatis_intro.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/dialer_whatis_intro.mspx?mfr=true))

Other questions around this have generated replies about SIP and VOIP which is not what I am after. How can I dial my landline phone using ubuntu?

That said, sould I be switching to a SIP/VOIP? I call Australia from Canada. I still want to be able to use my landline phone, can I plug that somehow into my computer if I switched to a SIP/VOIP?

Thanks.

FE

---

### Post by Chronon on 2009-09-06
How about dtmfdial in the repos?

> dtmfdial is a DTMF (Dual Tone Multiple Frequency) tone generator. This program generates the same tones that modern "TouchTone" telephones use to dial. It can be used to dial on any phone system supporting DTMF tones. dtmfdial requires a sound card to work, and is designed to be used as a phone dialer from address book

---

### Post by justborn on 2009-09-17
yes,i too am searching for the same thing. please help!

---

### Post by fisheater on 2009-09-17
I have yet to find one, or figure out how to use dtmfdial. I am a *nix novice and need GUI. I will try one of the windows opensource via wine and let you know how it went.

FE

---

### Post by Chronon on 2009-09-17
dtmfdial has a manpage.  After installing it do:
```
man dtmfdial
```

This will tell you what parameters to supply to run it properly.  If the defaults are all okay, you can just do "[FONT="Courier New"]dtmfdial *number*[/FONT]"  This will use your soundcard to play the sounds.

---

