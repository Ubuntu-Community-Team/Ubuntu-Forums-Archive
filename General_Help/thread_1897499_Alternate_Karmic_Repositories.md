---
title: "Alternate Karmic Repositories"
date: 2011-12-19
forum: General Help
---

### Post by FeraTech on 2011-12-19
Are the Karmic repositories no longer available? 

Are there any backup repositories I could use?

---

### Post by Paddy Landau on 2011-12-19
Karmic's support ended last April.

If you wish to use a single distro for a long time, please consider installing a Long-Term Support (LTS) version.

The last LTS was 10.04 (Lucid), which will be supported until 13.04. The next LTS due is 12.04 (Precise), which will be supported until 17.04.

You could try to upgrade Karmic to Lucid (be sure to back up your data first in case of problems), or you could wait until April and install 12.04 (I would recommend a fresh installation -- back up your data first).

---

### Post by FeraTech on 2011-12-19
This is a server install. I choose 9.10 sepcifically because the PHP version had the best compatibility.

Upgrading isn't an option. 

Are there any backup repos available?

---

### Post by Paddy Landau on 2011-12-19
Sorry, I am not aware of backup repositories. As Karmic is no longer supported, there is no longer support for its repositories.

Besides, if your 9.10 was fully up-to-date, there will be nothing more available anyway.

You could try opening your Software Sources, and in the Updates tab, select Proposed Updates and Unsupported Updates. However, as the names imply, you may find that these updates break your system or parts of it, so you use it at your own risk.

As the problem is PHP compatibility, have you considered installing an older version of PHP on a newer installation of Ubuntu?

---

### Post by snowpine on 2011-12-19
FeraTech, when an Ubuntu release goes "end of life" its repositories are moved to old-releases.ubuntu.com.

Therefore you can change your mirrors in /etc/apt/sources.list to old-releases. This will allow you to install unsupported, obsolete applications from the unsupported, obsolete Karmic repos. There will never, ever be any bug fixes or security patches to old-releases, so use at your own risk!

I hope that answers your question. I strongly agree with the suggestion above to use the currently-supported LTS release. If you are concerned with "PHP compatibility" then you should also know that the older version of PHP in Ubuntu 9.10 has known security vulnerabilities that will never be patched. :(

---

### Post by Lars Noodén on 2011-12-19
> **snowpine said:**
> FeraTech, when an Ubuntu release goes "end of life" its repositories are moved to old-releases.ubuntu.com.

Therefore you can change your mirrors in /etc/apt/sources.list to old-releases...

So you will have to set /etc/apt/sources.list to the following:

```

deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse

```

---

### Post by klaatu on 2011-12-21
Lars, thank you, thank you, thank you.

Because of the hardware i am using I need to use Karmic.
When the repositories dissapeared, it created a massive headache for me. ](*,)

I tried for ages to work/find out what to do.
And in 3 short lines for my sources.list, you had the answer for me.

Your a true hero. \\:D/

---

### Post by Paddy Landau on 2011-12-21
> **klaatu said:**
> Because of the hardware i am using I need to use Karmic.
If 11.10 or, when April comes around, 12.04 do not work on your hardware, please consider [raising a bug report]("https://help.ubuntu.com/community/ReportingBugs"). This will help others with the same problem as you.

As your problem is solved, please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others with the same problem.

---

### Post by Lars Noodén on 2011-12-21
I'm glad it helped.  Keep in  mind that Karmic is no longer maintained so that you are on your own for security issues.  I would see if you can overcome the barriers and upgrade to 12.04 when the time comes.  That will get you 5 years of support.

---

