---
title: "Why doesn't lotus symphony install on 12.04"
date: 2012-06-11
forum: General Help
---

### Post by the great sayaman on 2012-06-11
i have lotus symphony downloaded however whenever i try to install it gives an error

dependency not satisfiable: libnotify1 (>=0.4.4)

---

### Post by Mark Phelps on 2012-06-11
If you're talking about the Windows product, you should have checked the WineHQ site first, to confirm that the app installs and runs OK.

The WineHQ page link below shows the app rated as garbage -- meaning, it's not going to install or work, no matter what you do:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=7992]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=7992")

---

### Post by wilee-nilee on 2012-06-11
It does surprisingly it needs to be the hardy version not the lucid.

Find the hardy version deb.

---

### Post by clayt0njknight on 2012-07-02
Long and short, here's how to install the *newest* version posted on IBM's page (or at least what worked for me)
-------------------------------------------------

1.) Download newest version.  If you have trouble finding the name of the file, just copy and paste this filename into a search bar in any web browser and it should point you to IBM's download page for it:

symphony_3.0.1-1lucid1_i386.deb

NOTE: There is no 64-bit version of this.

2.) Open your favorite terminal and:

sudo apt-get install build-essential
sudo apt-get install libnotify-bin
sudo apt-get install libstdc++6
sudo apt-get install ia32-libs

You may already have these packages installed, in which case move on.  Additional note: If you are running a 32-bit installation, you do not need to install the ia32-libs package as you already have all of the 32-bit packages installed on your system.  This package is for 64-bit distros only.

3.) cd to the directory your symphony download is housed.

4.) sudo dpkg -i --force-all symphony_3.0.1-1lucid1_i386.deb

Be warned, this thing is going to throw a serious fit about dependencies, so the next part is crucial to NOT breaking your ability to update the rest of the system (Linux likes to fix broken packages first, and will force you to remove Symphony next time you try to update.)

5.) sudo gedit /var/lib/dpkg/status

6.) Wait for the file to load (it's large) and search for symphony.

7.) Once you find the symphony, and remove it entirely.  

8.) Save and close.

9.) Reboot.  

Hopefully, after much annoyance from users, IBM will unf*ck the Symphony requirements to make it a little cleaner installation process.  Then again, it's still in "beta," and it's free.

---

### Post by zepelin on 2012-07-04
Thankz... i'm looking for this answer for 2 days.



> **clayt0njknight said:**
> Long and short, here's how to install the *newest* version posted on IBM's page (or at least what worked for me)
-------------------------------------------------

1.) Download newest version.  If you have trouble finding the name of the file, just copy and paste this filename into a search bar in any web browser and it should point you to IBM's download page for it:

symphony_3.0.1-1lucid1_i386.deb

NOTE: There is no 64-bit version of this.

2.) Open your favorite terminal and:

sudo apt-get install build-essential
sudo apt-get install libnotify-bin
sudo apt-get install libstdc++6
sudo apt-get install ia32-libs

You may already have these packages installed, in which case move on.  Additional note: If you are running a 32-bit installation, you do not need to install the ia32-libs package as you already have all of the 32-bit packages installed on your system.  This package is for 64-bit distros only.

3.) cd to the directory your symphony download is housed.

4.) sudo dpkg -i --force-all symphony_3.0.1-1lucid1_i386.deb

Be warned, this thing is going to throw a serious fit about dependencies, so the next part is crucial to NOT breaking your ability to update the rest of the system (Linux likes to fix broken packages first, and will force you to remove Symphony next time you try to update.)

5.) sudo gedit /var/lib/dpkg/status

6.) Wait for the file to load (it's large) and search for symphony.

7.) Once you find the symphony, and remove it entirely.  

8.) Save and close.

9.) Reboot.  

Hopefully, after much annoyance from users, IBM will unf*ck the Symphony requirements to make it a little cleaner installation process.  Then again, it's still in "beta," and it's free.

---

### Post by pmorton on 2012-07-18
> **clayt0njknight said:**
> Long and short, here's how to install the *newest* version posted on IBM's page (or at least what worked for me)
-------------------------------------------------


Sometimes you hunt and hunt for a solution - in this case to a problem I've experienced many times over the years with Symphony on 64-bit linux - and suddenly you hit on someone who has set out the perfect solution - in good detail and great clarity. 

Many  thanks, clayt0njknight. I'd love to be able to buy you a pint of English bitter.

---

### Post by joefidler on 2013-02-16
I have had some luck editing the 'depends' section of /var/lib/dpkg/status for this package to remove libnotify1 (and other "incorrect dependencies") rather than deleting the whole symphony package entry.  This allows Symphony to still appear in the installed packages list and be removed, apply fix packs etc.

Here is a section of my  /var/lib/dpkg/status under the 'Package: symphony' section: 

Depends: libasound2 (>> 1.0.14), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7-9ubuntu1), libcairo2 (>= 1.6.0), libdbus-1-3 (>= 1.1.1), libdbus-glib-1-2 (>= 0.74), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1-21), libgconf2-4 (>= 2.13.5), libglib2.0-0 (>= 2.12.0), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), libidl0, libpango1.0-0 (>= 1.20.5), libpng12-0 (>= 1.2.13-4), libsm6, libstdc++6 (>= 4.1.1-21), libx11-6, libxext6, libxft2 (>> 2.1.1), libxi6, libxinerama1, libxp6, libxrandr2 (>= 2:1.2.0), libxrender1, libxt6, libxtst6, zlib1g (>= 1:1.2.3.3.dfsg-1)

I like Symphony as it works well with MS Office files - often better than LibreOffice.

---

### Post by postenga on 2013-03-21
how can i remove it? sudo apt-get remove symphony_3.0.1-1lucid1_i386.deb and sudo dpkg -P symphony doesn't work. And i can't find it on synaptic.

---

