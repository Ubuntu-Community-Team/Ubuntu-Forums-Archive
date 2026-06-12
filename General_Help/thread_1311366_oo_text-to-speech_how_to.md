---
title: "oo text-to-speech :how to"
date: 2009-11-02
forum: General Help
---

### Post by justborn on 2009-11-02
i got this plugin from [http://linux.softpedia.com/get/Text-Editing-Processing/Word-Processors/OO-Text-To-Speech-10204.shtml]("http://linux.softpedia.com/get/Text-Editing-Processing/Word-Processors/OO-Text-To-Speech-10204.shtml")

[COLOR="Red"]how do i get this plugin to work on my desktop?[/COLOR]

it is supossed to be oo text-to- speech plug-in,but it isn't in the [http://extensions.services.openoffice.org/]("http://extensions.services.openoffice.org/").is this an unsubmitted extension?

i tried the[COLOR="Red"]tools - extension manager - add[/COLOR]but the neither the extension file i downloaded([COLOR="Red"]tar.bz2[/COLOR]),nor the files inside the archive are of the [COLOR="Red"]extension[/COLOR] type.

---

### Post by justborn on 2009-11-02
i googled abt and found many sites refer to the being of the same plug-in but no one has the installation procedure.(i must be fool,not to know how to install that, i guess)

its wierd,the existence of an OO text-to-speech is all over the web.(since when ?,i donno)
but the open office extention page has no reference to it.it suggests the use of alien macros(i.e festival).check it for urself at[http://extensions.services.openoffice.org/project/Read_Text](http://extensions.services.openoffice.org/project/Read_Text)

is the site out of maintenance,or what?
or ,am i wrong,the plug-in is not from the community?

---

### Post by justborn on 2009-11-04
guys, help me pleaseeeeeeeeeeeeeeeeeee

---

### Post by m4tic on 2009-11-04
i havent downloaded it but jst saw it was a tarball. i think you are supposed to compile it yourself

---

### Post by Giblet5 on 2009-11-04
Well, the [OO plugin site]("http://extensions.services.openoffice.org/project/Read_Text") explains how to use the espeak TTS engine, which installs by default.

Open a terminal window, enter the following command ```
espeak "If I give all of my money to jibblett 5 then I can fly."
```

There are better voices around...

---

### Post by t0p on 2009-11-04
I don't know about the plugin.  There's a program called **espeak** that does text-to-speak.  You'll need to install it:

```
sudo apt-get install espeak
```

---

### Post by nadalex on 2011-04-23
i just downloaded OO-TTS and also can't figure out how to install.
i've only found install instructions in italian.
has anyone installed this? is it better than espeak?

---

### Post by beew on 2011-04-23
> **Giblet5 said:**
> Well, the [OO plugin site]("http://extensions.services.openoffice.org/project/Read_Text") explains how to use the espeak TTS engine, which installs by default.

Open a terminal window, enter the following command ```
espeak "If I give all of my money to jibblett 5 then I can fly."
```There are better voices around...

Cool it works on LibreOffice too.  Voice sounds like Stephen Hawking. :)

---

