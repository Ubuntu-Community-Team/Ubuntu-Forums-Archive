---
title: "Thunderbird address book not in .thunderbird"
date: 2012-02-11
forum: General Help
---

### Post by Menti on 2012-02-11
Recently I moved away from Ubuntu, upstream into Debian and clean Gnome 3. 

Kept the whole home folder and copied it to my new distribution, piece by piece.

My surprise: when I open Thunderbird, all my contacts are gone. I have emails, configuration, everything, except my contacts.

I think that since TB became default in Ubuntu it had some kind of integration with Evolution Data Server and Ubuntu One. So I copy my Evolution data folder from Ubuntu into Debian. No joy. My contacts are still gone.

I have two complete Ubuntu backups (one is a manual copy, the other is Deja Dup), so my address book should be somewhere. 

**My question is, can someone point me to the location of the main TB address book in Ubuntu?**

A million thanks.

As a side note, I should say that moving the TB address book away from .thunderbird is pretty bad design and user-unfriendly.

---

### Post by fballem on 2012-02-11
Hi,

If you look under the .thunderbird folder, you will see a folder with random letters and numbers followed by .default.

This is your profile folder. If you look under that folder, you should find your address book.

Hope this helps,

---

### Post by decrepit on 2012-02-11
yep agree with fballem, I have abook.mab in that folder.
I'm running 10.04 lts

No idea why yours is missing.
Do you have abook.mab in the defaults directory????
If so TB isn't looking there for it, may be a difference in Debian???

---

### Post by Deuce1912 on 2012-02-11
Your thunderbird profile may be looking for a profile folder that is named differently. The folders are named randomly. You may need to go into "/home/YOUR-USER/.thunderbird/xxxxxx.default from your old profile.

Then copy the contents to the same area or directory of your new home folder.

That's usually what I have to do. I hope it works out for you.

- Deuce1912

---

### Post by Menti on 2012-02-11
Thanks, but it is nothing like that.

Thunderbird reads the profile perfectly. I have all my mails, extensions, accounts, everything. It is only the address book what is missing, because **those addresses are not kept in abook.mab anymore. **

I think that when Ubuntu started integrating TB with Evolution and Ubuntu One, it moved the main address book somewhere else. After TB gained U1 sync, I had FOUR address books instead of just two. 

* My "personal" addresses, which was was my main address book previously, now was empty. [BOOK ICON]

* The address book where TB automatically throws any email you get messages from. [BOOK ICON]

* Ubuntu One address book [WORLD ICON]

* Another address book whose name I don't remember [WORLD ICON]

Now, after copying the .thunderbird folder with abook.mab, I have ONLY THE TWO FIRST BOOKS. The synchronized, world-icon books are not in .thunderbird. And that's where Ubuntu had moved my contacts.

---

### Post by ottosykora on 2012-02-11
the addresses are indeed kept in abook.mab

However I had some problems with it while copying it from one place to other, as the permisssions get mixed up and TB was not able to read it even thught physically the abook was there.

To make it kind of pragmatic simple, I copied it to an usb stick with fat32 format, by that all permissions were lost, then copied it under my user back to the proper place inside the profile.

There is also one small snag with the abook, the name of the address book as it appears in the TB has to be same.

If this does not work, simply import the contents of the abook.mab placed in some other place into the abook.mab just created by the TB.

And for import and export functions, I recomend you the 'more functions for addressbook' extension, you can find it here: 
[http://nic-nac-project.de/~kaosmos/morecols-en.html](http://nic-nac-project.de/~kaosmos/morecols-en.html)



The two you mention 
>* My "personal" addresses, which was was my main address book previously, now was empty. [BOOK ICON]

* The address book where TB automatically throws any email you get messages from. [BOOK ICON]<

are in fact inside the abook.mab, just kind of separate subfiles or so, you can have more addressbooks in the abook.mab, the number i do not know, but I had once 8 and all was inside the abook.mab.
The names are important, I also has some issues when I copied some abook.mab from english speaking computer to german speaking one.

---

### Post by Rebelli0us on 2012-02-11
You may have more than 1 profile. Start TB with this command and check the profile path

thunderbird -profilemanager

---

### Post by Menti on 2012-03-24
I discovered the problem and I am leaving an explanation here, since it may be a very big problem for a lot of people.

I was right: **my Thunderbird contacts were not kept anywhere in Thunderbird folders anymore.**

It was the Evolution contact integration extension. It synced Thunderbird contacts with Evolution by moving contacts from Thunderbird to Evolution. Not copying, moving. 

**So Thunderbird contacts are in .local/share/evolution instead of .thunderbird.**
I had figured this out when I asked here, but I copied my old Evolution folder to my new Evolution install, and I didn't get my old contacts back, so I wasn't sure. Now I know the problem, I had to kill evolution server before replacing the folders. Next time I launched Evolution, my old Thunderbird contacts where there, so I could export them and get them back into Thunderbird.

Conclusion:

**EDS contact integration moves your contacts out of .thunderbird folder. Be very careful if you reinstall your operating system, you may lose your address book forever.**

---

