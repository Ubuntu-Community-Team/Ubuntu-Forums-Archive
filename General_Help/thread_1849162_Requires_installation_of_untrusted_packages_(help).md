---
title: "Requires installation of untrusted packages (help)"
date: 2011-09-23
forum: General Help
---

### Post by ahiung on 2011-09-23
It says "Requires installation of untrusted packages"
Details:
```
apt apt-transport-https apt-utils google-chrome-stable libqt4-dbus libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-xml libqtcore4 libqtgui4
```
What should I do?

---

### Post by dcstar on 2011-09-24
> **ahiung said:**
> **It** says "Requires installation of untrusted packages"
Details:
```
apt apt-transport-https apt-utils google-chrome-stable libqt4-dbus libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-xml libqtcore4 libqtgui4
```
What should I do?

What is "it"?

What are you trying to do?

---

### Post by ahiung on 2011-09-24
> **dcstar said:**
> What is "it"?

What are you trying to do?

Here is the full explanation

1. Update Manager comes up

2. Loading...Building Data Structures

3. Then I clicked "Install Updates"

4. Typed in password... Authenticate

5. An error sound comes up like *CHUMPS!*

6. Show this message:

**[SIZE="4"]Requires installation of untrusted packages[/SIZE]**

The action would require the installation of packages from not authenticated sources.

>Details
```
apt apt-transport-https apt-utils google-chrome-stable libqt4-dbus libqt4-designer libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-xml libqtcore4 libqtgui4
```
[x]Close

That's it, no more I can explain. :(

---

### Post by David Andersson on 2011-09-24
I googled the error message and found [http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/)

It looks very much like what you describe, and has a solution. Hope it works for you.

(By any chance, have you at some earlier point added a PPA? That is, used apt-add-repository or Other Software in Software Sources?)

---

### Post by hansdown on 2011-09-24
Hi ahiung.

It's because, the packages are "third party".

You need to choose, whether you trust, that the packages are safe, or not.

I'm thinking they are safe.

You will encounter this in the future.

Don't worry.

---

### Post by mcduck on 2011-09-24
> **hansdown said:**
> Hi ahiung.

It's because, the packages are "third party".

You need to choose, whether you trust, that the packages are safe, or not.

I'm thinking they are safe.

You will encounter this in the future.

Don't worry.

No, the error message is not because the packages are third-party, neither should you ever see the message if you do all the required steps when adding new software sources.

The message is simply a result from adding a new software repository, but not adding the signing key for that repository. As a result apt can't verify the packages from that source, and will pop up that error every time (regardless of if the packages you at the moment are installing/updating come from that specific repository or some other one).

Just add the missing key and the message won't show any more.

---

### Post by ahiung on 2011-09-24
> **David Andersson said:**
> I googled the error message and found [http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/)

It looks very much like what you describe, and has a solution. Hope it works for you.

(By any chance, have you at some earlier point added a PPA? That is, used apt-add-repository or Other Software in Software Sources?)
Oh Thank you, I'll do that later, now I still in fun time.
I did add many outer sources from pcsx2 but the one shown in the error is Google Chrome. dunno why rofl.

---

