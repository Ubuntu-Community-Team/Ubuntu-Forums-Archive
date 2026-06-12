---
title: "Enabling text file preview"
date: 2010-01-10
forum: General Help
---

### Post by heryatmadja on 2010-01-10
Hi all,

Hope I can get some pointer in doing this.

I am running Jaunty and trying to enable the (plain) text file preview (in the thumbnail image).

What I have done/checked:
a. Set Nautilus setting of Preview/Text Files to Always
b. Checked the file type, by displaying the Properties dialog and it shows up as 'text/plain'
c. Cleared the files under ~/.thumbnails/fail and kill all nautilus then restart nautilus.  Didn't work (however, it fixed some of my flv files thumbnails though)
d. Googled and found out a way to enable/disable the preview via gconf-editor (desktop/gnome/thumbnailers). However, I couldn't find an entry for 'text@plain'.  So naturally I tried to create one.  Couldn't find out a way to do this, cause adding a key doesn't create a new 'path' for 'text@plain'.
e. Figured out where the config files are stored for gconf-editor in ~/.gconf.  Sadly, I can't seem to find any file that shows the 'long entry of items under desktop/gnome/thumbnailers. I proceeded by creating a new folder named 'text@plain' use other entry xml config as a base. Didn't show up in gconf-editor.

At this point, I am assuming the way to solve this is still to add the 'key/entry' in the configuration.  However, I have no clue how to it (at least other alternatives).

Secondly, what 'command line' should I use/add in the config key/entry to generate the preview/thumbnail?

Any help at all?

---

### Post by balta on 2011-02-08
I'm Sorry I really can't give any help as this is only a bump.
I'm suffering from the very same issue under a fresh ubuntu 10.10 x64 install
Never had this issue before; quite strangely with same interface\visual settings on my laptop running ubuntu 10.04 x32 everything's fine.

Even more strange it's the fact that I can see, quite blurred to be honest, pdf files previews.

Anyone any clue?

---

### Post by balta on 2011-02-11
bump!

---

### Post by antofthy on 2011-02-18
I am having the exact same problem.

Text files are not displaying any text preview.
I think the gnome developers turned something off on purpose.

Yes Nautilus text preview is enabled.
No there are not .thumbnails/failed/  files
there are not even any normal thumbnails for these files either
Yes the files are plain text

Any while a 'plain image' generic thumbnail is shown, it is not a preview thumbnail.

How can I get it working again?




As a stop gap measure I have a nautilus script which generates a thumbnail image. It creates it in the .thumbnails/normal directory with the appropriate hashed filename, using imagemagick.  however i have to manually update the creation of the thumbnail and the reload the directory to see the new thumbnail.   It is not a good solution!

Any extra information to getting nautilus to generate or update thumbnails would be nice.  Perhaps even run a script when entering a directory (script can limit itself to local directories).

---

### Post by OzzyFrank on 2011-03-12
I wouldn't mind an answer to this myself, as many of the icon themes I've tried disable the text preview. I'd rather not make do with a theme I don't particularly like, just to get preview of text files back.

I've seen mention of 2 files in /**usr/share/icons/gnome/scalable/mimetypes**, but for me the ***scalable*** folder doesn't have ***mimetypes***, and in **/usr/share/icons/gnome/48x48/mimetypes** there is indeed a ***text-x-preview.svg***, but no ***text-x-preview._icon_*** (besides, earlier posts suggest even if you have all the folders and files listed, copying those 2 files over to the current theme's folder does nothing).

---

### Post by antofthy on 2011-03-14
I never changed themes, just using the default (for fedora not ubuntu), but somehow I don't think that is the problem.

The 48x48 icon  text-x-preview.png   seems to be the icon that Gnome Nautilus is displaying by default for text files, and is also the file I use in my 'manual create text thumbnail' script.

I have not been able to get automatic previews for text files working.

I did find a discussion that looks at how to set up an automatic thumbnail preview creation for some very specific file type...
  [http://ubuntuforums.org/showthread.php?t=76566](http://ubuntuforums.org/showthread.php?t=76566)

But it seems very complex, and I have not tried to apply it to "plain/text" icon generation.  Particularly as I do not understand python scripts they use in that discussion.

Hopefully someone could at least tell us the gnome thumbnailing program that is used to create text file preview icons.   That would be a start!

---

### Post by antofthy on 2011-03-14
I got it working.

First I am using my own text-thumbnailer   unless someone can tell me
how the system would normally thumbnail text files

That was installed into /usr/bin/text-thumbnailer  for the time being
with appropriate execute permssions.  The script takes two arguments.  File URI's for the file to thumbnail and the thumbnail PNG it is to create.

So to enable... I create a 'schema' file..  "text-thumbnailer.schemas"
The normal location is in the directory  /etc/gconf/schemas
which will be automatically read after a reboot too.

```
<gconfschemafile>
  <schemalist>
    <schema>
      <key>/schemas/desktop/gnome/thumbnailers/text@plain/enable</key>
      <applyto>/desktop/gnome/thumbnailers/text@plain/enable</applyto>
      <owner>text-thumbnailer</owner>
      <type>bool</type>
      <default>true</default>
      <locale name="C">
        <short></short>
        <long></long>
      </locale>
    </schema>
    <schema>
      <key>/schemas/desktop/gnome/thumbnailers/text@plain/command</key>
      <applyto>/desktop/gnome/thumbnailers/text@plain/command</applyto>
      <owner>text-thumbnailer</owner>
      <type>string</type>
      <default>/usr/bin/text-thumbnailer %u %o</default>
      <locale name="C">
        <short></short>
        <long></long>
      </locale>
    </schema>
  </schemalist>
</gconfschemafile>
```

Note the file includes the location of the text-thumbnailer executable.

Now load that schema file to the running gnome system

gconftool-2 --install-schema-file \
     /etc/gconf/schemas/text-thumbnailer.schemas

Now KILL any nautilus running.  Typically I use xkill on a nautilus window to ensure it is really dead!

When the nautilus restarts (or you restarted it with a launcher), my
text files were thumbnailed correctly -- Yeay


The only thing missing from these instructions is the thumbnailer script.

My own script is very rough, and not ready for publication. So if someone can tell us what program gnome is supposed to be using to thumbnail text files, we'll have a complete solution.

---

