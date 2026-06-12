---
title: "HOWTO: Change from spatial to browser behavior in nautilus"
date: 2006-06-16
forum: General Help
---

### Post by MarinaraOfDeath on 2006-06-16
Ok, I finally (finally!) found the program *gconf-editor* and altered the behavior to get Nautilus to browsing all the time. I really hate the spatial behavior, so this is great. 

But now I'm still left trying to figure out how to make it open a .pro file (RSI IDL source, in a plain text format). When I was stuck in spatial view, Nautilus would complain about it not having a .txt extension but being a plain text file. Well, they're not plain text, they're IDL source files in text format. How do I make Nautilus open then in Kate (which has a module for proper IDL syntax highlighting built in)? I've created a script that does it based on arnieboy's gedit-root script, but it's still a horrible kludge compared to single- or double-clicking the file to open. 

I would say that I hate to say this, but I'd be lying. Microsoft got this one right -- warn me, every time until I tell the warnings to go away, then give me enough rope to hang myself. Failing that, since it isn't all that secure, don't cost me hours trying to get a piece of software to do what I want.

;;----------------------------------------------------------------------

**UPDATE**: Adding more detail, here's the quick way to change Nautilus's behavior.
[LIST=1]
[*]Open a terminal.
[*]Type the command ```
which gconf-editor
```, which will print out the path to the command. For me, this is /usr/bin/gconf-editor, but at the time I didn't know where it was. which is awesome, because it searches the paths contained in the PATH environment variable for a command. If a command is installed, you should be able to see where it is using which. Check to make sure where your installation put the command.
[*]I tend to copy-paste for this sort of stuff, so I just copied the line printed as the output of the previous step. If you're in a standard terminal, copy is Ctrl+C, I believe, while paste is Shitf+Insert unless you've remapped it like I have since I use the fish shell.
[*]You should now see a GUI with a tree in the left pane that has four entries: apps, desktop, schemas, system. Expand the tree for Apps by clicking the triangle. Scroll down to nautilus and expand that tree too. (It's amusing to geeks with too much time on their hands to note that there are at least three ways of telling the GUI to expand a tree. :D Cross-platform geeks will notice how easily Windows registry hacking skills will make it to alter these settings.)
[*]Still in the left pane, scroll down to the entry labeled preferences. As you go through each one it will show the possible changes currently available.
[*]Now click on the checkbox in the right pane, the one that says always_use_browser. Exit the program, and the next time you start nautilus by whatever method you choose, you'll always get browser bahvior, such as in the Places menu.
[/LIST]

;;----------------------------------------------------------------------

**UPDATE**: The above is the third and the nicest rendition, by a long shot, of what I was dealing with. Eventually enough googling has gotten me through. 

[LIST]I read a bit on defining and registering MIME types. Following the instructions at [http://gnomesupport.org/forums/viewtopic.php?t=10921](http://gnomesupport.org/forums/viewtopic.php?t=10921), I created a file called pro.xml in ~/.local/share/mime/packages containing the text

> <?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
	<mime-type type="text/pro">
		<comment xml:lang="en">RSI ISL procedure source file</comment>
		...
		<magic priority="50">
			<match type="string" value="\x89PRO" offset="0"/>
		</magic>
		<glob pattern="*.pro"/>
		<desktop:can-edit-with>kate.desktop</desktop:can-edit-with>
	</mime-type>
</mime-info>
You can do the same for your file extension by changing the proper information in my example above (the example I altered was written for opening png images in Gimp). I haven't quite figured out what the <desktop: > tags indicate yet, as sources are mixed. It might just be a part of the spec that never caught on and so got removed?

[*]Then I ran
```
update-mime-database ~/.local/share/mime/
``` 
The information that pointed me towards gconf-editor was at [http://www.gentoo-wiki.com/HOWTO_Gnome_Desktop_Admin_Guide](http://www.gentoo-wiki.com/HOWTO_Gnome_Desktop_Admin_Guide). I rebooted, due to needing one after software update, then fired up Nautilus via the Places menu.

[*]The last step was to associate the .pro filetype with Kate, which unlike everything in this rigaramole claimed to be easily done, was actually easily done by right-clicking and going through the standard procedure just as if in Konqueror or in Windows.
[/LIST]
;;----------------------------------------------------------------------

---

