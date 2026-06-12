---
title: "Evolution does not load image in signature"
date: 2009-08-10
forum: General Help
---

### Post by Stoneface on 2009-08-10
I use a signature for several email accounts with a LinkedIn profile image. It does load in Thunderbird but not in Evolution. Here is the html code:
```

<a href="http://www.linkedin.com/in/myprofile" >
          <img src="http://www.linkedin.com/img/webpromo/btn_profile_greytxt_80x15.gif" width="80" height="15" border="0" alt="View My profile on LinkedIn">
    </a>

```

Any ideas why this online image does not load in Evolution?

Another annoying thing is that Rhythmbox temporarily stops playing or cuts the online radio connection when I load an e-mail.

NB Solutions offered here: [http://ubuntuforums.org/showthread.php?t=912255](http://ubuntuforums.org/showthread.php?t=912255) did not help either. All images are now always loaded and there is a direct connection to the internet.

---

### Post by Stoneface on 2009-08-10
I found a bug report on the loading of external images here: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/391095](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/391095) bu says it is a duplicate of another I can't find yet.. red hat has the same issue tracked here though: [https://bugzilla.redhat.com/show_bug.cgi?id=398021](https://bugzilla.redhat.com/show_bug.cgi?id=398021)

---

### Post by stinger30au on 2009-08-10
> **Stoneface said:**
> I use a signature for several email accounts with a LinkedIn profile image. It does load in Thunderbird but not in Evolution. Here is the html code:
```

<a href="http://www.linkedin.com/in/myprofile" >
          <img src="http://www.linkedin.com/img/webpromo/btn_profile_greytxt_80x15.gif" width="80" height="15" border="0" alt="View My profile on LinkedIn">
    </a>

```Any ideas why this online image does not load in Evolution?.


it wouldnt be something simple like the settings for email are set to plain text and not show html at all??

---

### Post by Stoneface on 2009-08-11
@ Stinger30AU The plain text mode under Edit > Preferences > Mail preferences > HTML Messages is set to "show HTML if present". Format message in HTML is checked under Edit > Preferences > Composer Preferences >  General. And last but not least all my signatures are in HTML format. So that all seems to be as it should be to make an external image appear in a signature..


P.S. I just had an Evolution error. I wonder if the signature issue and the error are related:

```
[97587.696393] evolution[17646]: segfault at 4 ip b6bc4f50 sp bfba1230 error 4 in libgobject-2.0.so.0.2000.1[b6bb8000+3c000]
```

---

### Post by dcstar on 2009-08-12
> **Stoneface said:**
> I use a signature for several email accounts with a LinkedIn profile image. It does load in Thunderbird but not in Evolution. Here is the html code:
```

<a href="http://www.linkedin.com/in/myprofile" >
          <img src="http://www.linkedin.com/img/webpromo/btn_profile_greytxt_80x15.gif" width="80" height="15" border="0" alt="View My profile on LinkedIn">
    </a>

```

Any ideas why this online image does not load in Evolution?

Because you probably did not create your sig using HTML mode and using the tools for inserting links.

---

### Post by process91 on 2010-07-02
The original poster probably already found the answer to his question, but I found this thread as a result of the same problem and wanted to leave my solution here.

It's a simple matter of HTML mode being turned off in multiple places. If you make sure that HTML mode is on for
[LIST=1]
[*]Composing messages (Preferences -> Composer Preferences -> Format messages in HTML)
[*]The signature itself (Preferences -> Composer Preferences -> Edit signature -> Format -> HTML)
[*]Displaying messages (Preferences -> Mail Preferences -> HTML Messages -> Always load images from the Internet)
[/LIST]

you should have no problem! I noticed that even with all of the above settings in place, the image does not appear in the signature editing area or composer window, but it does appear on the recipient's side.

---

### Post by ricaxe on 2011-09-08
thanks ... for the info

---

