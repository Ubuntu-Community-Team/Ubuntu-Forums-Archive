---
title: "Mutt - Quick 'n Easy?"
date: 2006-03-03
forum: General Help
---

### Post by az_human on 2006-03-03
Does anybody have a guide to configuring Mutt / Sendmail / Postfix / etc etc etc for  standard pop3 / smtp access?  At first I would rather be able to configure it to send and receive email without getting dirty doing so... because I like to dig around and play afterwards.

I have looked on Mutt.org and Postfix.org but I cannot find any guides that explain in any quick and easy manner.

I do understand the value of learning before or as you are setting things like this up... but to be honest, either I am overlooking the simplicity of it all or it is too complex for me at the moment.  Maybe my attention span just isn't there right now, I don't really know... but I do know I would like to get Mutt working for simple email functions.  I love using the terminal for things that can otherwise be done in an oftentimes overrated graphical interface.

I wouldn't describe myself as a total newbie to the Linux world... I've been dabbling in it off and on for quite a few years now, most of the time switching back to Windows after a certain level of irritation would set in from the Linux learning curve... but after coming back to Linux time and time again, it gets easier each time.  I now run Ubuntu as my primary OS with a Windows XP VMWare image that I can run at any time should I need anything from it.  Works great.  I don't have to boot out of Linux to do so -- so in my situation it's much better than dual booting as I have in the past considering I'm not a gamer.

Anyhoo, thanks for listening to me babble and any input on a simple quick 'n easy dummy guide to configuring Mutt and anything else needed for it would be greatly appreciated!  I lurk every day in ubuntuforums.org and enjoy reading the posts immensely.

---

### Post by John.Michael.Kane on 2006-03-03
[http://linux.ucla.edu/guides/mailguide.php3](http://linux.ucla.edu/guides/mailguide.php3)
[http://home.nyc.rr.com/computertaijutsu/mutt.html](http://home.nyc.rr.com/computertaijutsu/mutt.html)
[http://codesorcery.net/mutt/mutt-gnupg-howto](http://codesorcery.net/mutt/mutt-gnupg-howto)
[http://www.gentoo.org/doc/en/guide-to-mutt.xml](http://www.gentoo.org/doc/en/guide-to-mutt.xml)
[http://www.siliconvalleyccie.com/linux-hn/sendmail.htm](http://www.siliconvalleyccie.com/linux-hn/sendmail.htm)
[http://www.faqs.org/docs/linux_network/x-087-2-sendmail.html](http://www.faqs.org/docs/linux_network/x-087-2-sendmail.html)
[http://www.sonicresolutions.com/tech/howto_postfix_vmpop3d.html](http://www.sonicresolutions.com/tech/howto_postfix_vmpop3d.html)

---

### Post by rune_kg on 2006-10-06
hey az-human

follow this howto until "PGP", and you are up and running:

[http://wiki.sourcemage.org/HOWTO-Setup_mutt%2Bprocmail%2Bfetchmail%2Bgnupg%2Bmsmtp]("http://wiki.sourcemage.org/HOWTO-Setup_mutt%2Bprocmail%2Bfetchmail%2Bgnupg%2Bmsmtp")

if your smtp host does not require authenciation, change your .msmtprc to:

defaults
auth off
account accountname
host smtp.something.xyz

---

### Post by andrew.46 on 2007-07-02
Hi,

 This is quite an old post but I have actually posted just such a guide:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

                      Andrew

---

