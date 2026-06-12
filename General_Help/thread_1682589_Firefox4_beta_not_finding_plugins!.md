---
title: "Firefox4 beta not finding plugins!"
date: 2011-02-06
forum: General Help
---

### Post by santosh83 on 2011-02-06
Hello all,

Although I use the system's default version of Firefox (v3.6), I wanted to give the Firefox4 beta a test drive, so I downloaded it from Mozilla and extracted it into my ~/bin directory.

However it seems that Firefox4 is not able to pick-up the plugins installed for the system version. All the plugins currently installed for Firefox3.6 are in /usr/lib/mozilla/plugins/, with a couple of symlinks to other places, so I can't figure out why the beta is not able to find them. I thought /usr/lib/mozilla/plugins/ was a standard directory for Firefox plugins on Linux.

I also tried copying one plugin (Flash) file from /usr/lib/mozilla/plugins/ to ~/.mozilla/plugins/ and to ~/bin/firefox/plugins/, but still Firefox4 is not finding it. About:plugins is blank, as is the plugins tab of the Add-on manager.

Any help is appreciated. By the way, I'm using the same profile for both Firefox3.6 and Firefox4. Is this fine, or should I create a separate profile for use with the beta version?

Thanks.

P.S. For what it's worth, my system is a 64-bit one, running 64-bit Ubuntu 10.10.

---

### Post by [Snc] on 2011-02-06
> **santosh83 said:**
> Hello all,

Although I use the system's default version of Firefox (v3.6), I wanted to give the Firefox4 beta a test drive, so I downloaded it from Mozilla and extracted it into my ~/bin directory.

However it seems that Firefox4 is not able to pick-up the plugins installed for the system version. All the plugins currently installed for Firefox3.6 are in /usr/lib/mozilla/plugins/, with a couple of symlinks to other places, so I can't figure out why the beta is not able to find them. I thought /usr/lib/mozilla/plugins/ was a standard directory for Firefox plugins on Linux.

I also tried copying one plugin (Flash) file from /usr/lib/mozilla/plugins/ to ~/.mozilla/plugins/ and to ~/bin/firefox/plugins/, but still Firefox4 is not finding it. About:plugins is blank, as is the plugins tab of the Add-on manager.

Any help is appreciated. By the way, I'm using the same profile for both Firefox3.6 and Firefox4. Is this fine, or should I create a separate profile for use with the beta version?

Thanks.

P.S. For what it's worth, my system is a 64-bit one, running 64-bit Ubuntu 10.10.

Have you followed the installation procedure given to you?

I too run multiple (all three) versions: 3.6, 4.0beta(10???) and 4.012pre and all use the same profile, so they share plugins, themes, bookmarks etc.

My guess would be, that there is something wrong with the permissions and ownerships of files... check that out.

For a quick install of flash 64b without hassle, take a look at flash-aid (after sorting stuff out with the above mentioned problems)


Enjoy!

---

### Post by santosh83 on 2011-02-06
> **'[Snc] said:**
> Have you followed the installation procedure given to you?

I too run multiple (all three) versions: 3.6, 4.0beta(10???) and 4.012pre and all use the same profile, so they share plugins, themes, bookmarks etc.

My guess would be, that there is something wrong with the permissions and ownerships of files... check that out.

For a quick install of flash 64b without hassle, take a look at flash-aid (after sorting stuff out with the above mentioned problems)


Enjoy!

Thanks for the reply. I simply extracted the archive (as supplied by mozilla) into my ~/bin/ directory. Did nothing else in terms of installation, except for adding a menu entry, pointing to the firefox executable.

Firefox beta *is* picking up the extensions I'm using with the default version (noscript, adblock etc). It's the plugins which are not being found and/or loaded.

It's surprising that Firefox4 isn't finding the plugins even when I copy them to ~/.mozilla/plugins/ or FIREFOX4_DIR/plugins! Let me try again.

Well, it still doesn't work. This time I made sure to change ownership of the plugins I copied over from /usr/lib/mozilla/plugins/ into ~/.mozilla/plugins/ from root to myself, but they're still not being recognised by Firefox4. Hmm... very mysterious.

Thanks for your reply. I'll keep tinkering around and see if I can find something out.

---

### Post by [Snc] on 2011-02-06
have you checked
```
about:plugins
```and 

```
about:addons
```?

Becouse FF4 can run most plugins, just the developers did a "*not so good*" of a job, setting the flag for the max version (most still have 3.6b set!)

---

### Post by santosh83 on 2011-02-06
> **'[Snc] said:**
> Have you followed the installation procedure given to you?

I too run multiple (all three) versions: 3.6, 4.0beta(10???) and 4.012pre and all use the same profile, so they share plugins, themes, bookmarks etc.

My guess would be, that there is something wrong with the permissions and ownerships of files... check that out.

For a quick install of flash 64b without hassle, take a look at flash-aid (after sorting stuff out with the above mentioned problems)


Enjoy!

By the way, I've already got the Flash 64-bit "square" preview from Adobe Labs installed. That was the flash binary I copied over from /usr/lib/mozilla/plugins into ~/.mozilla/plugins/.

Everything is flawless with the system default Firefox3.6, but I just wanted to test out the HTML5 features of Firefox4. Now if I can get this plugin issue solved, my day will be made. :-)

---

### Post by [Snc] on 2011-02-06
As i said, some extensions are disabled, because they are "incompatible"

(If you have the original XPI files, you can edit a XML inside, to make it "*compatible*")

PS. HTML5 is flash unrelated :) FF4 and Minefield already support it.

---

### Post by [Snc] on 2011-02-06
The above mentioned XPI is "install.rdf"

find this
        <em:maxVersion>**3.5.***</em:maxVersion>
modify to
        <em:maxVersion>**4.0.***</em:maxVersion>

Use at your own risk ;)

---

### Post by santosh83 on 2011-02-06
> **'[Snc] said:**
> The above mentioned XPI is "install.rdf"

find this
        <em:maxVersion>**3.5.***</em:maxVersion>
modify to
        <em:maxVersion>**4.0.***</em:maxVersion>

Use at your own risk ;)

Yes, as you said, it seems that Firefox4 is simply rejecting some plugins. Tried copying over the vlc plugin, to the same effect.

The above instructions can only be done for extensions I think, correct me if I'm wrong? As I said, all the extensions are carrying over from Firefox3.6 to beta without problems! It's the plugins that are not being found or recognised. Yes, I tried about:addons too, which opens up the addons page. The extensions are correctly listed, but the plugins tab is blank.

Unfortunately editing the install.rdf file won't be possible with the plugins I think.

Thanks for your suggestions. I'll try asking in Mozilla's forum maybe, or see if there an about:config setting I can tweak! :-)

---

### Post by [Snc] on 2011-02-06
I get this as a result ...

PS. no, the rdf file is present only in XPI files (zip archive)

---

### Post by santosh83 on 2011-02-06
> **'[Snc] said:**
> I get this as a result ...

PS. no, the rdf file is present only in XPI files (zip archive)

Yes! I've all those plugins installed in Firefox3.6, but I'm getting a blank tab in Firefox4!

By the way, have you simply left the plugins in their default location (which I suppose is /usr/lib/mozilla/plugins/), for all Firefox versions, or have you copied them over to other places?

If your system is also Maverick 64-bit, then my problem would be really strange, as it ought to work as it does for you!

Additionally, you've just extracted Firefox4 into a folder, without any other additional setup right?

Maybe starting Firefox4 with a new profile will solve this issue... let me see.

Thanks.

---

### Post by [Snc] on 2011-02-06
all 6 are in /usr/lib/mozilla/plugins/
1 of them is a symlink (libjavaplugin.so) to /etc/alternatives/mozilla-javaplugin.so

And yes, I have Maverick 64b with a 64b Minefield from nightly.mozilla.org

---

### Post by santosh83 on 2011-02-07
Well, finally I've found the cause. While my system is 64-bit, the official binary supplied by Mozilla is a 32-bit build. While extensions are in source form, and therefore loaded, the plugins of course are 64-bit binaries, and they don't load. Starting the beta from the command-line (instead of through an icon) produced these revealing error messages:

LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-cone-plugin.so [/usr/lib/mozilla/plugins/libtotem-cone-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so [/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so: wrong ELF class: ELFCLASS64]
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libtotem-mully-plugin.so [/usr/lib/mozilla/plugins/libtotem-mully-plugin.so: wrong ELF class: ELFCLASS64]

... and so on.

It seems Mozilla will not provide *official* 64-bit release builds of Firefox until version 4 is released. So onto [ftp://ftp.mozilla.org/pub/firefox/nightly/latest-mozilla-central/](ftp://ftp.mozilla.org/pub/firefox/nightly/latest-mozilla-central/) for the nightly builds!

Thanks all!

---

