---
title: "Can anyone help me out with a Python plugin?"
date: 2010-04-27
forum: General Help
---

### Post by bkadoctaj on 2010-04-27
This plugin is not one I started but it seems like it's 99.9% done.  It was made for Rhythmbox and what it is supposed to do is help the user organize the files in his/her library.  As I'm sure some of you know, this is a long-demanded feature for Rhythmbox that might allow it to fully eclipse Banshee.

The plugin is called "fileorganizer" and it can be found here: [https://launchpad.net/rb-fileorganizer](https://launchpad.net/rb-fileorganizer)

Now, what happens is the file organizer is supposed to create directories and then copy renamed files into them according to user specification.  Unfortunately, as the plugin currently stands, it just creates the directories but does not actually move the files.  I haven't heard back for the developer of the plugin so I don't know what he has to say about that.  Nonetheless, I have a feeling it is just one small line of code that is ****ed up or missing.  Could anyone take a look into it?

I suspect the issue can be found here, in the fileops.py code:
```
#!/usr/bin/env python
#
#       Author:    Wolter Hellmund
#       Email:    wolterh6@gmail.com
#       --------------------------------------
#       Fileorganizer file operations
#       --------------------------------------
#       Creative Commons

import os, shutil, urllib
import rhythmdb
import tools

metatypes = ('artist','album','title','track')

class Musicfile ():

    def __init__ (self, fileorganizer, db_entry=None):
        self.fo = fileorganizer
        db = self.fo.db
        if db_entry:
            self.metadata = {
                metatypes [0]:    db.entry_get (db_entry, rhythmdb.PROP_ARTIST),
                metatypes [1]:    db.entry_get (db_entry, rhythmdb.PROP_ALBUM),
                metatypes [2]:    db.entry_get (db_entry, rhythmdb.PROP_TITLE),
                metatypes [3]:    db.entry_get (db_entry, rhythmdb.PROP_TRACK_NUMBER)
            }
            self.location = db.entry_get (db_entry, rhythmdb.PROP_LOCATION)

    # Returns metadata of the music file
    def get_metadata (self,key):
        for datum in self.metadata:
            if key == datum:
                return self.metadata [datum]

    # Moves the file to a specific location with a specific name
    def relocate (self):
        # Configure path
        targetdir = self.fo.configurator.get_val ('folder')
        targetdir = tools.datafiller (self, targetdir)
        targetdir = tools.folderize (self.fo.configurator, targetdir)
        # Configure name
        targetname = self.fo.configurator.get_val ('file')
        targetname = tools.datafiller (self, targetname)
        targetname += os.path.splitext (self.location)[1]
        # Relocate, if necessary
        source = urllib.url2pathname(self.location).replace ('file:///','/')
        destin = os.path.join (self.fo.configurator.get_val ('dir'), \
            targetdir, targetname)
        # Debugging purposes only
        #~ print 'Location: '+urllib.url2pathname (self.location).replace ('file:///','/')
        #~ print 'Destination: '+os.path.join (self.fo.configurator.get_val ('dir'),targetdir,targetname)
        if source == destin:
            print 'No need for file relocation'
        else:
            if os.path.isfile (destin):
                # Copy the existing file to a backup dir
                backup = os.path.join (os.path.dirname (destin),'backup',os.path.basename (destin))
                try:
                    os.makedirs (os.path.dirname (backup))
                except:
                    pass
                shutil.copy2 (destin, backup)
            print 'Relocating file %s to %s' % (source,destin)
            # Move
            shutil.move (urllib.url2pathname(self.location).replace ('file:///','/'), \
                os.path.join(self.fo.configurator.get_val('dir'),targetdir,targetname))
            # Remove empty folders, if any
            sourcedir = os.path.dirname (source)
            if os.listdir (sourcedir) == []:
                print '%s (directory) now empty; removing' % sourcedir
                os.rmdir (sourcedir)
            else:
                print '%s (directory) still contains files; keeping' % sourcedir
```Please, please... someone help with this haha.  This is such a crucial and useful feature.  If we could just get this plugin working...  I don't know Python so I'm currently at a loss for how to read this code.  :(

Thanks in advance.  :D

Also, the bug report I filed is here and it has debug info:
[https://bugs.launchpad.net/rb-fileorganizer/+bug/567708](https://bugs.launchpad.net/rb-fileorganizer/+bug/567708)

---

### Post by bkadoctaj on 2010-04-28
No one?  Okay, look, I did a little digging yesterday and I realized that the problem with the code is that there is an int value drawn when attempting to organize by track number... how can this be converted to a string type and where would I place that into the code?  I really could use someone's help.  Thanks.  :)

---

### Post by th5th on 2010-04-28
> **bkadoctaj said:**
> No one?  Okay, look, I did a little digging yesterday and I realized that the problem with the code is that there is an int value drawn when attempting to organize by track number... how can this be converted to a string type and where would I place that into the code?  I really could use someone's help.  Thanks.  :)

I think your bug is in the db.entry_get() function called in __init__:

```

    def __init__ (self, fileorganizer, db_entry=None):
        self.fo = fileorganizer
        db = self.fo.db
        if db_entry:
            self.metadata = {
                metatypes [0]:    db.entry_get (db_entry, rhythmdb.PROP_ARTIST),
                metatypes [1]:    db.entry_get (db_entry, rhythmdb.PROP_ALBUM),
                metatypes [2]:    db.entry_get (db_entry, rhythmdb.PROP_TITLE),
                metatypes [3]:    db.entry_get (db_entry, rhythmdb.PROP_TRACK_NUMBER)
            }
            self.location = db.entry_get (db_entry, rhythmdb.PROP_LOCATION)

```> File "/home/jason/.gnome2/rhythmbox/plugins/fileorganizer/tools.py",  line 24, in datafiller
      string = string.replace (('$'+key),process (file.get_metadata  (key)))
File "/home/jason/.gnome2/rhythmbox/plugins/fileorganizer/tools.py",  line 31, in process
     string = string.replace ('/','_')
AttributeError: 'int' object has no attribute 'replace'
(From the debug on Launchpad).

So this means tools.process() is being called with an int rather than str (I guess - string is a pretty unhelpful name for a string...). That means file.get_metadata(key) is returning an int not a str. Since get_metadata just accesses the self.metadata dictionary (though it's a pretty nasty accessor - heard of "if key in dict"?) you can assume the values returned by db.entry_get are ints (sometimes or all the time) not strs.

And there my Python fu ends, since db.entry_get() is presumably defined wherever the fileorganizer argument to __init__ has come from...

Join #python on IRC (Freenode). I know at least one Python master who used to hang out on there, and I assume there are many more...

---

### Post by bkadoctaj on 2010-04-28
> **th5th said:**
> I think your bug is in the db.entry_get() function called in __init__:

```

    def __init__ (self, fileorganizer, db_entry=None):
        self.fo = fileorganizer
        db = self.fo.db
        if db_entry:
            self.metadata = {
                metatypes [0]:    db.entry_get (db_entry, rhythmdb.PROP_ARTIST),
                metatypes [1]:    db.entry_get (db_entry, rhythmdb.PROP_ALBUM),
                metatypes [2]:    db.entry_get (db_entry, rhythmdb.PROP_TITLE),
                metatypes [3]:    db.entry_get (db_entry, rhythmdb.PROP_TRACK_NUMBER)
            }
            self.location = db.entry_get (db_entry, rhythmdb.PROP_LOCATION)

```(From the debug on Launchpad).

So this means tools.process() is being called with an int rather than str (I guess - string is a pretty unhelpful name for a string...). That means file.get_metadata(key) is returning an int not a str. Since get_metadata just accesses the self.metadata dictionary (though it's a pretty nasty accessor - heard of "if key in dict"?) you can assume the values returned by db.entry_get are ints (sometimes or all the time) not strs.

And there my Python fu ends, since db.entry_get() is presumably defined wherever the fileorganizer argument to __init__ has come from...

Join #python on IRC (Freenode). I know at least one Python master who used to hang out on there, and I assume there are many more...

Definitely sometimes.  Only the track number metadata is returned as an int.  Thanks for the input.  I'll drop by IRC then.

EDIT:  Well, they basically suggested I start learning to program...

Damn it... if I had more time I would but I just need to fix this one small thing...  :(

EDIT 2: Hmm, replacing this line
```
db.entry_get (db_entry, rhythmdb.PROP_TRACK_NUMBER)
```
with
```
str(db.entry_get (db_entry, rhythmdb.PROP_TRACK_NUMBER))
```
seemed to do the trick!  Not completely sure though...

Now another issue is the fact that Rhythmbox doesn't realize that the plugin renamed the files and moved them, so two copies of the track appear in Rhythmbox but only one exists.  The original one appears as missing (of course, because it's no longer there with the name it originally had).  How can I fix the code so that the database realizes this?

---

