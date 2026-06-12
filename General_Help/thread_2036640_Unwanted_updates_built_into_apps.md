---
title: "Unwanted updates built into apps"
date: 2012-08-02
forum: General Help
---

### Post by Exomancer on 2012-08-02
I use Ubuntu 12.04 and have LibreOffice installed.

Background:
LibreOffice comes with Turkish built in and locked.  Why, I don't know :confused:.  I speak English not Turkish.  So I found out how to permanently remove Turkish from my LibreOffice install.  This worked perfectly and I have no problems with LibreOffice :D.

However, the Ubuntu Update Manager constantly wants to install an update for the no longer installed LibreOffice Turkish :(.  Obviously this is coming from LiberOffice or Ubuntu since I installed LiberOffice from the Ubuntu repositories. 

My Question:
Is there a way to set Update Manager like Windows Update Manager.  To remove or hide an unwanted update from future updates.  In this case I don't mean removing LiberOffice.  I want LibreOffice.  I just don't want the Turkish package which I now have to scan through every update (sometimes 40-60 entries) to AGAIN uncheck it so it does not install or I'll have to remove it again after every update ](*,).

Thanks.

---

### Post by Cheesehead on 2012-08-02
> **Exomancer said:**
> Update Manager constantly wants to install an update for the no longer installed LibreOffice Turkish

Update Manager does not update or reinstall pacakages you removed properly. 

How, exactly, did you remove Turkish? If you simply deleted it, then the system is properly trying to repair the (it's perspective) damage. If you used apt-get to remove the langpack, then you should not be prompted for an update.

---

### Post by JosephBeck on 2012-08-02
Also, LibreOffice should be automatically installed with your Ubuntu, did you remove it to reinstall it? I have it on here by default and theres nothing about Turkish o-o....Naturally in English. If your  LibreOffice has everything in English you shouldn't have need to mess with the extra languages that come with it.

---

### Post by gandaran on 2012-08-02
hi
try setting up the system language properly in system settings » language support, put English at the top and remove Turkish, you may need to reboot then.

---

### Post by Exomancer on 2012-08-02
Thanks for your replies.

> How, exactly, did you remove Turkish?From the instructions online I just deleted it in the directory manually.

> LibreOffice should be automatically installed with your Ubuntu.It was but not Base.  Also going to the Software Center it showed that the meta-package was not installed but the three components were installed.  I did not know if I should just install the components or the meta-package.  Also I did not know what would happen if I installed the meta-package on top of an existing install.  So I removed LiberOffice and reinstalled it with the meta-package from the Ubuntu Software Center.  Also see my post about the Ubuntu Software Center.  This is an example of what I was talking about in that post.

[http://ubuntuforums.org/showthread.php?p=12146159#post12146159](http://ubuntuforums.org/showthread.php?p=12146159#post12146159)

> system language properly in system settingsI checked that and all is set to English.  Turkish is nowhere to be found.  I did however also find a Slovenian dictionary under User-Defined Dictionaries.  I don't speak Slovenian any more than I do Turkish and I have no idea how I have a user-defined Slovenian dictionary.  Nor can I delete it from the GUI any more than I could the Turkish pack.

OK so using the langpack clue I found the issue.  With Synaptic I found that the Turkish langpack was still installed in my system and yes it was trying to repair it. <snip> In my opinion, the Ubuntu Software Center is not adequate and needs a Synaptic level of detail, even if you had to hide and un-hide it.

Thank you guys!  Especially [Cheesehead]("http://ubuntuforums.org/member.php?u=425951")!

---

