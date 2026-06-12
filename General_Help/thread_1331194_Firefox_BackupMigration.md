---
title: "Firefox Backup/Migration"
date: 2009-11-19
forum: General Help
---

### Post by Quarkrad on 2009-11-19
Thanks to this forum I discovered how easy it is to save firefox bookmarks/passwords and reinstall onto a new ubuntu system (e.g. clean intall from 9.04 TO 9.10).  As easy as copying the contents of /home/.mozilla from  one to other.  I have convinced a friend to change from winxp to ubuntu but not sure how to do the same with winxp's firefox.  On xp you have Documents & Settings/USER NAME/Application Data/Mozilla  and then a number of sub folders containing all sorts.  Does anybody know if it is possible to copy some of these winXP firefox folder/files to Ubuntu's /home/.mozilla so that the user has his/her 'old' firefox back?

---

### Post by John Bean on 2009-11-19
> **Quarkrad said:**
> Thanks to this forum I discovered how easy it is to save firefox bookmarks/passwords and reinstall onto a new ubuntu system (e.g. clean intall from 9.04 TO 9.10).  As easy as copying the contents of /home/.mozilla from  one to other.  I have convinced a friend to change from winxp to ubuntu but not sure how to do the same with winxp's firefox.  On xp you have Documents & Settings/USER NAME/Application Data/Mozilla  and then a number of sub folders containing all sorts.  Does anybody know if it is possible to copy some of these winXP firefox folder/files to Ubuntu's /home/.mozilla so that the user has his/her 'old' firefox back?

Yes. Depending on what you need, some contents of the profile can be copied. In fact the whole profile can be copied, but it will cause a few problems (but only a few) because of saved paths for things like downloads that are saved in the format of the host. A quick scan through the Firefox settings on the new host afterwards soon puts things right.

Incidentally it's only the Firefox profiles folder I'm talking about. not the whole Mozilla hierarchy. On Ubuntu this is stored in {$HOME}/.mozilla/Firefox and on XP is in %APPDATA%\Mozilla\Firefox - note that the absolute path varies across differing versions of Windows.

Edit: The above assumes the same version of Firefox is being used - changes were made in data format across versions.

---

### Post by lovinglinux on 2009-11-19
> **John Bean said:**
> Yes. Depending on what you need, some contents of the profile can be copied. In fact the whole profile can be copied, but it will cause a few problems (but only a few) because of saved paths for things like downloads that are saved in the format of the host. A quick scan through the Firefox settings on the new host afterwards soon puts things right.

Additionally, several extensions are OS dependent. You can use [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension to backup the most important settings or the full profile. Nevertheless, I don't recommend a full backup if you plan to use the profile on another OS. Anyway, FEBE allows you to easily backup only what you need (passwords, cookies, permissions, bookmarks and so on).

---

### Post by John Bean on 2009-11-19
> **lovinglinux said:**
> Additionally, several extensions are OS dependent.
True, although in my experience Firefox will detect and disable them along with any with version dependencies. Having said that, I wasn't aware of FEBE before I read your reply, so...
> Anyway, FEBE allows you to easily backup only what you need (passwords, cookies, permissions, bookmarks and so on).
I haven't tried it yet, but from what you say this is definitely the way to go, removing all the guesswork and pitfalls of copying profile data.

---

### Post by lovinglinux on 2009-11-19
> **John Bean said:**
> True, although in my experience Firefox will detect and disable them along with any with version dependencies.

I'm not sure about that, because there is nothing OS specific in the extension installation file. Just as an example, here is one of my extensions install.rdf file:

```

<?xml version="1.0"?>

<RDF xmlns="http://www.w3.org/1999/02/22-rdf-syntax-ns#" xmlns:em="http://www.mozilla.org/2004/em-rdf#">

  <Description about="urn:mozilla:install-manifest">

    <em:id>fmc@fmc.isgreat.org</em:id>
    <em:version>3.2.0</em:version>
    <em:optionsURL>chrome://fmc/content/options.xul</em:optionsURL>
    <em:name>FoxMediaCenter</em:name>
    <em:description>A lightweight media center extension</em:description>
    <em:creator>lovinglinux</em:creator>
    <em:homepageURL>http://fmc.isgreat.org</em:homepageURL>
    <em:iconURL>chrome://fmc/content/images/logo.png</em:iconURL>
    <em:targetApplication>
      <Description>
        [COLOR="Red"]<em:id>{ec8030f7-c20a-464f-9b0e-13a3a9e97384}</em:id>[/COLOR]
        <em:minVersion>3.5</em:minVersion>
        <em:maxVersion>3.6a1</em:maxVersion>
      </Description>
    </em:targetApplication>

  </Description>

</RDF>

```

The line in red declares that the extension is designed for Firefox. The two subsequent  lines are responsible for telling Firefox if the extension is compatible with your Firefox version or not.

If you compare it with a Windows only extension like IETab, you can see that the declarations are the same:

```
   <em:id>{77b819fa-95ad-4f2c-ac7c-486b356188a9}</em:id>
   <em:name>IE Tab</em:name>
   <em:version>1.5.20090525</em:version>
   <em:description>Enables you to use the embedded IE engine within Mozilla/Firefox.</em:description>
   <em:creator>Hong Jen Yee (PCMan)</em:creator>
   <em:developer>yuoo2k</em:developer>
   <em:homepageURL>https://addons.mozilla.org/firefox/addon/1419</em:homepageURL>
   <em:optionsURL>chrome://ietab/content/ietabSetting.xul</em:optionsURL>
   <em:iconURL>chrome://ietab/skin/ietab-icon.png</em:iconURL>

   <!-- Firefox -->
   <em:targetApplication>
     <Description>
       [COLOR="Red"]<em:id>{ec8030f7-c20a-464f-9b0e-13a3a9e97384}</em:id>[/COLOR]
       <em:minVersion>3.0</em:minVersion>
       <em:maxVersion>3.5.*</em:maxVersion>
     </Description>
   </em:targetApplication>
```

Besides, if we want to upload multiple OS versions of an extension to Mozilla Add-ons site, we must specify, in the upload form, for which OS it is designed. So only the site can choose the correct one based on the user system info. 

> **John Bean said:**
> I haven't tried it yet, but from what you say this is definitely the way to go, removing all the guesswork and pitfalls of copying profile data.

Yep, FEBE is great. It also allows you to perform daily/weekly/monthly automated backups and to create a backup every time you open and/or close Firefox.

---

### Post by John Bean on 2009-11-19
Perhaps you're right - probably without the "perhaps!. It's a while since I last did it but now that I think about it I seem to recall it did indeed install IETab on the Linux box - which of course didn't work although it didn't break anything either. After removing unused (and inapplicable) addins and correcting the paths it worked flawlessly and has continued to do so.

But it's a moot point now that there's a simpler, safer way to do the task. Thank you again for the pointer.

---

