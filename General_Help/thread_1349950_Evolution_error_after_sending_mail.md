---
title: "Evolution error after sending mail"
date: 2009-12-08
forum: General Help
---

### Post by gregk1963 on 2009-12-08
Hi all.
After sending mail using Evolution I get the following error:

Failed to append to mbox:#EVO_USERDATADIR#/mail/local#Sent: URL 'mbox:#EVO_USERDATADIR%23/mail/local%23Sent' needs a path component Appending to local `Sent' folder instead.

Even though the mail is being sent; it's annoying...
Any help would be appreciated.
Thanks

---

### Post by farstrider on 2009-12-15
I am having the same problem exactly with a clients PC and it's really starting to piss me off! The only thing I can thiink off that MAY be the cause of the problem is that I had 9.10 installed on the PC  and after a **** storm of problems, backed up the mail and docs etc. I reinstalled 9.04 on the thing and duely resrored the mail to Evolution and since then had the same message after a send. Them Evolution died altogether...... and so the story goes on...! I now have everything working again but still get the error message when sending. The mail does however go and I seem to receive the mail on my side no problem. The real problem that lies with you is when the client keeps asking why these errors can not be resolved!

Thanks

---

### Post by farstrider on 2009-12-16
gregk1963 asked this question a week ago, does NO ONE have this problem?? This must be the most unique occurrence in the history of Ubuntu releases!!

Anyone :? Has anyone seen this or have an idea of what could be causing this? Please I would be extremely grateful for some assistance regarding this problem!

Thank you!

---

### Post by philinux on 2009-12-16
Bit of google. 

[http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=eDb&q=failed+to+append+to+mbox%3A%23EVO_USERDATADIR&btnG=Search&meta=&aq=f&oq=](http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=eDb&q=failed+to+append+to+mbox%3A%23EVO_USERDATADIR&btnG=Search&meta=&aq=f&oq=)

**_Possible fix_**.

[http://www.debuntu.org/how-to-fixing-evolution-after-home-directory-changed-failed-to-append-to-mbox](http://www.debuntu.org/how-to-fixing-evolution-after-home-directory-changed-failed-to-append-to-mbox)

gconf-editor runs from the terminal or from system>tools if you activate the menu item.

Personally I would check gconf for errors regarding the path.

---

### Post by farstrider on 2009-12-16
Thank for the reply philinux, but that "solution" has nothing to do with the problem that I am having. when I redid the installation I used identical user names etc to make absolutely certain that I did not have any conflicting info from one install to the other. I give up, thanks anyway! This is the sort of thing that makes Linux for the average user a joke. I am reasonably au fait with most of my day to day stuff but certain things like this, well ...... anyway as I said I am now done with this! 

Thanks for taking the time to help. Cheers.

---

### Post by Kooster on 2010-02-05
It's easier than I thought. Open Evolution/edit/preferences/accounts, then choose your account/edit/defaults, then use the Drafts folder and Sent Messages folder buttons. On each button a dropdown list appears. From there you can pick the correct folder for each, all is funky again. No more crappy, irratating, lowdown error message. 
It worked for me and I can't see why it won't work for others too.

GOOD LUCK!!!!

"Don't de-evolutionize"

---

### Post by chomps on 2010-03-03
Thank you Kooster,

I have had this exact same problem for months...It is when you upgrade to evolution mail in ubuntu 9.10 and back up your mail and then go back to 9.04 and import the mail and settings. For some reason 9.10 writes the imported file (.tar.gz) in a nother way.

Your post worked for me.


Chomps

---

