---
title: "antivirus?"
date: 2010-12-09
forum: General Help
---

### Post by joelkat on 2010-12-09
I would like a antivirus possibly a very good free one?

---

### Post by karthick87 on 2010-12-09
Use clamav,
```
sudo apt-get install clamav clamtk
```

---

### Post by wojox on 2010-12-09
[Antivirus]("https://help.ubuntu.com/community/Antivirus")

---

### Post by I'mGeorge on 2010-12-09
well ClamAV it's pretty much the only open source antivirus for linux. Usually under Linux you shouldn't have problems with viruses that's the reason of having to write the administrator password almost all the time.  But check this list out to see the available antiviruses for linux [http://en.wikipedia.org/wiki/List_of_antivirus_software](http://en.wikipedia.org/wiki/List_of_antivirus_software)

---

### Post by joelkat on 2010-12-09
i only found KlamAV and like you can get viruses from websites...

---

### Post by deanjm1963 on 2010-12-09
Ubuntu (linux) is not Windows. It's unlikely that you'd ever get a virus from a website. The viruses themselves don't have permission to run on a linux machine.

And as karthick87 suggested (these programs are in the repositories)

```
sudo apt-get install clamav clamtk
```

from a terminal or use Synaptic to install the programs.

---

### Post by dmizer on 2010-12-09
> **joelkat said:**
> [snip] you can get viruses from websites...

Not even remotely likely. Even more unlikely if you practice safe browsing habits.

Here's some more reading. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by karthick87 on 2010-12-09
As far as i know clamav will be good.But sometimes CLAMAV will give false positive result.So be sure before you delete the infected file.

---

### Post by Rubi1200 on 2010-12-09
> **dmizer said:**
> Not even remotely likely. Even more unlikely if you practice safe browsing habits.

Here's some more reading. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
+1 Absolutely right!!

If you want to make your browser more secure, see bodhi.zazen's post here:
[http://ubuntuforums.org/showthread.php?t=671604](http://ubuntuforums.org/showthread.php?t=671604)

---

### Post by sammiev on 2010-12-10
I have always used avast with windows and now the version they have for lunix can aslo scan lunix and windows at the same time if you are running a dual boot system. GL :D Best to scan if you are sharing files with friends and family still using windows.

---

### Post by bodhi.zazen on 2010-12-10
> **jriano said:**
> There is more than ClamAv, now you can install Avast and AVG.
[http://juanriano.com/post/1677728641/free-linux-antivirus]("http://juanriano.com/post/1677728641/free-linux-antivirus")

Or you can relax and enjoy Linux. I have been using Linux for some time and have never had a problem with viruses. period.

---

### Post by dcstar on 2010-12-10
> **bodhi.zazen said:**
> Or you can relax and enjoy Linux. I have been using Linux for some time and have never had a problem with viruses. period.

I scan my e-mails for Viri using Clamav just so I can have a laugh at the things out there waiting to attack Windows systems.

As well, it identifies Phishing scams with bogus links in the e-mail body:

[http://ubuntuforums.org/showthread.php?t=1363102](http://ubuntuforums.org/showthread.php?t=1363102)

---

### Post by bodhi.zazen on 2010-12-10
> **dcstar said:**
> I scan my e-mails for Viri using Clamav just so I can have a laugh at the things out there waiting to attack Windows systems.

As well, it identifies Phishing scams with bogus links in the e-mail body:

[http://ubuntuforums.org/showthread.php?t=1363102](http://ubuntuforums.org/showthread.php?t=1363102)

Nice one. At least you know how to use av properly.

I often feel new users get more FUD then quality advice on "viruses" on linux. They are all too often encouraged to use antivirus "just in case".

Antivirus makes sense on a file or mail server, which is basically how you are using it (as a filter on mail).

---

### Post by StephenG on 2010-12-16
I've also had good luck with BitDefender.  They have anti-spam for mail servers.  Here's the link:
[http://www.bitdefender.com/site/Search/?query=unices&x=0&y=0](http://www.bitdefender.com/site/Search/?query=unices&x=0&y=0)

---

### Post by ssulaco on 2010-12-16
> **joelkat said:**
> i only found KlamAV and like you can get viruses from websites...No


> **bodhi.zazen said:**
> Or you can relax and enjoy Linux. I have been using Linux for some time and have never had a problem with viruses. period.+1


joelkat....this is a good read
[http://linuxmafia.com/~rick/faq/index.php?page=virus](http://linuxmafia.com/~rick/faq/index.php?page=virus)

---

