---
title: "how to make firefox feel like old firefox in 10.10"
date: 2010-05-16
forum: General Help
---

### Post by 133794m3r on 2010-05-16
ok since ubuntu's decided that firefox needs to have their strange and weird theme for the buttons... what's the easiest way to remove this new way that it decides that the button configuration for when you want to close it and other things? I cannot seem to find this file, and i've already tried to delete my .mozilla file and i've installed swiftfox and it's using it. So where in the world did the Ubuntu UI people put this thing at?

---

### Post by dcstar on 2010-05-16
> **133794m3r said:**
> ok since ubuntu's decided that firefox needs to have their strange and weird theme for the buttons... what's the easiest way to remove this new way that it decides that the button configuration for when you want to close it and other things? I cannot seem to find this file, and i've already tried to delete my .mozilla file and i've installed swiftfox and it's using it. So where in the world did the Ubuntu UI people put this thing at?

There are probably hundreds of posts on changing the window buttons in 10.04 (they affect everything, not just Firefox), search them out.

---

### Post by mkvnmtr on 2010-05-16
You can remove Firefox and the related programs. I use synaptic. Search firefox and look for installed programs. Then use the Ubuntuzilla site to enable a repository the current Mozilla Firefox. Or if you wish you can use Swiftfox. It is the current Debian firefox release. Either one of those should give you a Firefox without the Ubuntu branding.

---

### Post by lovinglinux on 2010-05-16
Firefox UI can be changed by adding special instructions to the file userChrome.css, which is under the chrome directory of Firefox profile folder (i.e. ~/.mozilla/firefox/<profilename>).

You will find several tutorials out there that recommend adding the following code to that file:

```
.dialog-button-box {-moz-box-direction: reverse !important; -moz-box-pack: right !important;}

.dialog-button-box spacer {display: none !important;}
```

Unfortunately, this doesn't solve the problem completely, since the buttons are placed on the left side instead of the right. I couldn't find a solution yet.

---

### Post by lovinglinux on 2010-05-16
> **dcstar said:**
> There are probably hundreds of posts on changing the window buttons in 10.04 (they affect everything, not just Firefox), search them out.

I think the user is referring to Fiefox Cancel/OK button position (see my previous post), but I thought this was a KDE modification only.

> **mkvnmtr said:**
> Or if you wish you can use Swiftfox. It is the current Debian firefox release. Either one of those should give you a Firefox without the Ubuntu branding.

I think you are confusing it with Iceweasel. Swiftfox is a proprietary project and is not included in the Debian repositories or the Ubuntu repositories.

---

