---
title: "security confusion"
date: 2011-03-02
forum: General Help
---

### Post by flipper T on 2011-03-02
as a relatively new convert to all things ubuntu, i have a few security related issues that have left me confused:

1 i have read warnings in these forums regarding installation of .deb files and the use of ppa's....other than possible system instability, is there an actual security risk involved here?

2 viruses...i do not dual boot or send .exe's to windows pcs....is there any reason at all to install anti-virus software ?

3 spyware...basically same question as no.2

4 i read that linux is not vulnerable to viruses ? is this absolutely true or is only in comparison to windows....if so why all the security updates ?

5 i use the web of trust (WOT) extension in chromium and firefox...can i merrily disregard any warnings regarding dodgy websites ?... occasionally stumble into such sites accidently :)

---

### Post by seawolf167 on 2011-03-02
1. Don't install untrusted software. Someone could make the software do anything they want (i.e. bot your machine), so don't install that .deb from that guy you talked to on IRC. Most of the "actual" software out there is good however.

2. There are no *nix virus' in the wild atm, though thats not to say that they [don't exist and never have]("http://www.neowin.net/news/a-history-of-viruses-on-linux"). You can install antivirus, but you most likely don't need it (clamav comes to mind). The vast vast vast majority of virus' are targeted at Win machines simply because of their market share.

3. See #2. Most bad malware will take advantage of things like ActiveX.

4. See the link in #2 for the *nix virus history.

5. Not sure what the web of trust extension is, so I can't say for sure, but you should never disregard common sense. If something seems fishy or too good to be true, it probably is.

Misc. security patches are for fixing errors in programing. Say you use SSH, you don't want a flaw to exist that allows someone to bypass you authentication procedures and thus negate your SSH security because of some weird programing mistake or omission.

---

### Post by flipper T on 2011-03-02
thanks for your comprehensive and informative reply

interesting link too

---

