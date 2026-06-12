---
title: "Plugins for aleks.com dont work"
date: 2009-09-03
forum: General Help
---

### Post by Thebiggz on 2009-09-03
I've been trying to get this to work for a couple days now and I can't figure it out. this is the command line i did [php]cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/ext/
[/php] When I add sudo nothing even happens. I get this error every time though. [php]cp: cannot create regular file `/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/ext/aleksPack10.jar': Permission denied
[/php] Any help would be appreciated.

---

### Post by punkdrummer09 on 2009-10-20
Um, I'm not too sure if this work, but try this in your terminal:

su root(it should ask for your password)

then  		 			[COLOR=#000000] [COLOR=#0000BB]cp aleksPack10[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]jar [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]usr[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]lib[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]jvm[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]java[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]6[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]sun[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]1.6.0.14[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]jre[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]lib[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]ext[/COLOR][COLOR=#007700]/  [/COLOR][/COLOR]

---

### Post by punkdrummer09 on 2009-10-20
or you can just do this: (just make sure to check your java version; in your case it's probably java-6-sun-1.6.0.14 instead of .16)

i did this: sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/ext/

but for you it's: sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/ext/

---

