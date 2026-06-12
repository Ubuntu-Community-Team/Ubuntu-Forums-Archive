---
title: "Phatch - help please"
date: 2010-12-04
forum: General Help
---

### Post by hundred1906 on 2010-12-04
Does anyone know how to make Phatch retain the input directory structure for its output? So that the new files are structured under a new header folder in the same way as the originals.

Ditto for using it to reduce photo resolution. Ie make JPG files  smaller so they are quicker to access from a MythTV front end. Is that Scale, Save, Cut or ....?

How do I use Nautilus-Phatch - I cannot see any options in the menus?

---

### Post by stani on 2010-12-04
> **hundred1906 said:**
> Does anyone know how to make Phatch retain the input directory structure for its output? So that the new files are structured under a new header folder in the same way as the originals.

Ditto for using it to reduce photo resolution. Ie make JPG files  smaller so they are quicker to access from a MythTV front end. Is that Scale, Save, Cut or ....?

How do I use Nautilus-Phatch - I cannot see any options in the menus?
- folder structure: use <subfolder> e.g. 
```
<folder>_phatch/<subfolder>
<root>/phatch/<subfolder>
```
- you can reduce the size of the images with 'Scale' or you want can reduce the quality in the Save action (when jpeg is selected).
- phatch-nautilus should allow you to export actions to the context menu, but it is not working atm

If you don't see the menu in Phatch, start Phatch from the command line and first type:
```
export UBUNTU_MENUPROXY=0
```

---

### Post by hundred1906 on 2010-12-22
Thanks for the reply and sorry for my delay but have been away.

Unfortunately your assistance is not very clear to me.

In your reply about folder structure does this mean that it is not possible to do this from inside the Phatch PHoto bATCH Processor GUI. Also then how do I use the code examples you give eg "<folder>_phatch/<subfolder>" Where does this code get used as I cannot see from the Man page an option telling Phatch how to create the output directory structure?

I cannot find phatch-nautilus as an application or as an extension to Nautilus on my system even though Synaptic reports it as installed. No doubt it is obvious but where do I find and use it?

Where you suggest "If you don't see the menu in Phatch ..." what menu do you mean and where should I be looking for it?

Regards.

---

### Post by GrouchyGaijin on 2011-01-30
I've got the same question.  I see that, according to synaptic, I have the phatch nautilus scripts installed.  However, where exactly are they?

They are not in the ~/.gnome2/nautilus-scripts/ folder.
I thought they would be accessible like the other nautilus scripts I have installed.

On a slightly different note, Phatch no longer remembers which action files I've run.  Each time I launch Phatch I need to navigate to the folder containing my action files and choose the one I want.  I used to have an option to choose from recently used action files.  Does anyone know how to get that back?

I'm running Phatch 2.7.2 under Ubuntu 10.10.

---

### Post by GrouchyGaijin on 2011-01-30
bump

---

### Post by kernst on 2011-04-07
> **GrouchyGaijin said:**
> I've got the same question.  I see that, according to synaptic, I have the phatch nautilus scripts installed.  However, where exactly are they?

```
dpkg -l | grep phatch
```

will tell you the name of the package, if you weren't sure to begin with. It's **phatch-nautilus**.

```
dpkg -L <packagename>
```

will list the contents of the package. So, from the listing of [FONT="Courier New"]**dpkg -L phatch-nautilus**[/FONT] I see:

```
...
/usr/share/phatch/phatch/lib/linux/nautilusExtension.py
```

which tells me that this is a *Phatch* extension, *not* a Nautilus script (contrary to the words "Nautilus scripts" in the package description). I believe what this is supposed to do is allow you to export a Phatch action list *as* a Nautilus script (*i.e.*, create a script in ~/.gnome2/nautilus-scripts that would run the Phatch action list on the selected files).

If the package were functional (and stani said above it isn't currently), it would probably manifest itself in a similar fashion to *Action List -> Export -> Action List Droplet...*, which creates a [FONT="Courier New"].desktop[/FONT] file in the folder of your choosing you can use to drag-and-drop files on and run an action list on them. Make sense?

---

### Post by kernst on 2011-04-07
> **hundred1906 said:**
> In your reply about folder structure does this mean that it is not possible to do this from inside the Phatch PHoto bATCH Processor GUI. Also then how do I use the code examples you give eg "<folder>_phatch/<subfolder>" Where does this code get used as I cannot see from the Man page an option telling Phatch how to create the output directory structure?

Perhaps a screenshot will help. See below. The example I've given saves a scaled version of all selected images in a subfolder called "00_SCALED_800px" (created at the same level in the directory structure as the selected images), recreating all subfolders in the destination tree (if you told it to descend into subfolders when you ran the action).

Once you add a "Save" action to the end of your action list, you will see the option to create filename suffixes and subfolders. There is quite a lot of flexibility in how this works, and I can't imagine a case where you'd be unable to create the desired target directory structure given the options in Phatch.

These variables may be useful to help your understanding (from [http://photobatch.wikidot.com/variables):](http://photobatch.wikidot.com/variables):)

> [LIST]
[*]<filename>
[*]<folder> (the folder given in the execute dialog box, within a hierarchy this is fixed)
[*]<foldername> (the basename of the folder)
[*]<subfolder> (the relative path of the image in regards to <folder>, within a hierarchy this changes)
[*]<root> (the parent folder of <folder>, within a hierarchy this is fixed)
[*]<path> (the absolute path of the image)[/LIST]

as would this note from the same page:

> To be clear, these expressions for the absolute path are all equal:

<path>
<folder>/<subfolder>/<filename>.<type>
<root>/<foldername>/<subfolder>/<filename>.<type>

For an example, open an image the Image Inspector and you will be able to inspect all these values.



> **hundred1906 said:**
> I cannot find phatch-nautilus as an application or as an extension to Nautilus on my system even though Synaptic reports it as installed. No doubt it is obvious but where do I find and use it?

> **stani said:**
> - phatch-nautilus should allow you to export actions to the context menu, but it is not working atm

Stani (who, I presume, is the author of Phatch, so he'd know) mentioned above that the package currently doesn't do what it's supposed to at the moment. Which is allow you to export a Phatch action list *to* the Nautilus context menu (right click on a file in Nautilus -> "Scripts"). I explain this in more detail (with a screenshot) in my earlier reply. I have phatch-nautilus installed on a 10.04 system and nothing shows up in my Phatch menus either.

---

