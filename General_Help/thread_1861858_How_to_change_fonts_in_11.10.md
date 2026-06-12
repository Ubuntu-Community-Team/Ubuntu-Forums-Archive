---
title: "How to change fonts in 11.10"
date: 2011-10-16
forum: General Help
---

### Post by Tares on 2011-10-16
Hello,

as the tittle says, how to change fonts in the system ? Without installing gnome-tweak-tools.

---

### Post by mcduck on 2011-10-16
> **Tares said:**
> Hello,

as the tittle says, how to change fonts in the system ? Without installing gnome-tweak-tools.

Well, you pretty much ruled out the best solution in your question.

Gnome3 has no built-in tool for the purpose, Gnome-Tweak-Tool is the best option and officially supported by Gnome.

Perhaps the option is configurable somewhere in dconf. You could install dconf-tools and try browsing around in the dconf-editor in case you find anything, although I definitely haven't stumbled upon such option there.

---

### Post by Tares on 2011-10-16
Well, I guess its time to change distro. Thanks.

---

### Post by 3rdalbum on 2011-10-16
> **Tares said:**
> Well, I guess its time to change distro. Thanks.

I'd say that's about the weakest excuse for distro-hopping that I've ever heard. Honestly.

Besides, where would you go? Gnome 3 doesn't ship with anything that modifies the fonts. Gnome 3 distros will either not ship with a font selector, or will ship with Gnome Tweak Tool. Gnome 2 won't be around forever.

Bottom line: You want to change your fonts, you want Gnome Tweak Tool. There's no getting around it, and threatening to change distro won't help anybody.

---

### Post by fantab on 2011-10-16
> **Tares said:**
> Well, I guess its time to change distro. Thanks.

Good Luck.:)

---

### Post by Tares on 2011-10-17
> **3rdalbum said:**
> I'd say that's about the weakest excuse for distro-hopping that I've ever heard. Honestly.

Besides, where would you go? Gnome 3 doesn't ship with anything that modifies the fonts. Gnome 3 distros will either not ship with a font selector, or will ship with Gnome Tweak Tool. Gnome 2 won't be around forever.

Bottom line: You want to change your fonts, you want Gnome Tweak Tool. There's no getting around it, and threatening to change distro won't help anybody.

Lol. I didn't threated anyone. Just stated the fact. Icon issue isn't the first thing that makes me rage with this ubuntu update.

For now I've installed xubuntu and I'm testing crunchbang on virtualbox, so maybe I'll change to that. I'm to lazy to switch to anything not debian based.

---

### Post by philinux on 2011-10-17
> **Tares said:**
> Hello,

as the tittle says, how to change fonts in the system ? Without installing gnome-tweak-tools.

What is your aversion to this package?

---

### Post by Tares on 2011-10-17
> **philinux said:**
> What is your aversion to this package?

Thanks for your time, but I've switched to Xubuntu for now. Topic can be closed, without a solution.

Btw. I didn't want to install gnome-tweak-tool, because it wanted to install many packages that I didn't want.

---

### Post by mjuhasz on 2011-10-17
Fonts can be changed with gconf-editor and dconf-editor. The four keys you want to change:

3 in dconf-editor under org/gnome/desktop/interface: font-name, document-font-name and monospace-font-name

1 in gconf-editor under /apps/metacity/general: titlebar_font

I know it's rather technical but the average user will install gnome-tweak-tools anyway. I did not want the gnome-shell dependency so I did it this way.

---

### Post by Tares on 2011-10-18
> **mjuhasz said:**
> Fonts can be changed with gconf-editor and dconf-editor. The four keys you want to change:

3 in dconf-editor under org/gnome/desktop/interface: font-name, document-font-name and monospace-font-name

1 in gconf-editor under /apps/metacity/general: titlebar_font

I know it's rather technical but the average user will install gnome-tweak-tools anyway. I did not want the gnome-shell dependency so I did it this way.

I guess thats make the topic solved. Thanks.

---

### Post by johnsmoke on 2011-10-18
I still have Ubuntu 11.04, so I'm not sure if this will still work. But to add fonts I wanted, I just created a hidden folder (.fonts) in my Home Folder, and added fonts into that.

---

