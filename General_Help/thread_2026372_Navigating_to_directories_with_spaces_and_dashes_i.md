---
title: "Navigating to directories with spaces and dashes in name"
date: 2012-07-15
forum: General Help
---

### Post by Weidbrewer on 2012-07-15
Hi, all.  Trying to fix a problem with my Plex Media Server.  The instructions say to delete the following files to let the system rebuild them:

```
Delete "$PLEX_HOME/Library/Application Support/Plex Media Server/Plug-ins/System.bundle"
Delete "$PLEX_HOME/LibraryApplication Support/Plex Media Server/Plug-ins/Framework.bundle" 
```

Now, these files are located in folders that have dashes and spaces in them and I need to delete from the command line - so I can't figure out how to get to them.

To explain, the folder in question is located at (if you read it literally):

```
/var/lib/plexmediaserver/Library/Application Support/Plex Media Server/Plug-ins
```

Obviously, I can't cd to that because of the formatting.  I can get as far as "Library," but then I'm stuck.  Even trying to see what the system calls it gets me nothing:

```
me@home:/var/lib/plexmediaserver/Library$ ls
Application Support

```

I'm sure it's something obvious - can anyone help?

---

### Post by Kirk Schnable on 2012-07-15
You need to use escape characters. 

/path/to/folder with spaces/ 

Becomes

/path/to/folder\ with\ spaces/

Kirk

---

### Post by mcduck on 2012-07-15
...or just use quote marks before and after the path/file name. :)

for example: 
```
rm "$PLEX_HOME/Library/Application Support/Plex Media Server/Plug-ins/System.bundle"
```

Also using the Tab key to autocomplete paths, filenames and commands makes things like this easier, as it will automatically add the quotes (and of course saves you from lots of typing).

---

### Post by Kirk Schnable on 2012-07-15
> **mcduck said:**
> ...or just use quote marks before and after the path/file name. :)

for example: 
```
rm "$PLEX_HOME/Library/Application Support/Plex Media Server/Plug-ins/System.bundle"
```

Also true. I just don't like doing it that way as much. I think it's better practice to know and understand what escape characters are. That way is cheating. 8)

Kirk

---

### Post by Weidbrewer on 2012-07-15
And, that'll do it.  Thanks, guys!

---

### Post by Kirk Schnable on 2012-07-15
> **Weidbrewer said:**
> And, that'll do it.  Thanks, guys!

Glad we could be of assistance!

---

