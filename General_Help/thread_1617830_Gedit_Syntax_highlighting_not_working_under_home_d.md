---
title: "Gedit Syntax highlighting not working under /home/ directory"
date: 2010-11-09
forum: General Help
---

### Post by jmlagace on 2010-11-09
I've been battling with this weird problem for a while now and since I can't seem to find a decent answer I'm hoping one of you guys can steer me in the right direction.

The problem is simple... syntax highlighting is not working consistently on ".rb" files.

My user name on my Ubuntu 10.04 LTS is jean-marc

So if I do
touch /home/jean-marc/testing.rb 

and then 
gedit /home/jean-marc/testing.rb

the file comes up as "Plain Text"

if I copy the file into /tmp/ and do gedit /tmp/testing.rb
the file comes up as "Ruby"

If I do 
gedit /home/jean-marc/afile.rb 
and the file does not exists the file comes up as "Ruby"

If I manually set the Syntax Highlight mode on my file gedit seems to remember it.

Something afoot here and I can't seem to grasp the problem.  Since most of the files are generated through scripting they all come as "Plain Text" and it's definitely not the best way to edit them.

Also, the files, no matter where they are show up as "Ruby script (application/x-ruby)" when showing the attributes through nautilus

Now, before someone tells use, use this software or that software instead of gedit, well I'm happy with the tool and its plugins. I'm efficient with it and I'd rather stick to it.

Ideas? anyone?

---

### Post by pvincent on 2011-02-19
Sorry, but I can't found a solution either.
You've mentioned something related to application/x-ruby.
What does it mean exactly ?
Is this a fix for the trouble.

---

### Post by dcstar on 2011-02-19
> **jmlagace said:**
> I've been battling with this weird problem for a while now and since I can't seem to find a decent answer I'm hoping one of you guys can steer me in the right direction.

The problem is simple... syntax highlighting is not working consistently on ".rb" files.

My user name on my Ubuntu 10.04 LTS is jean-marc

So if I do
touch /home/jean-marc/testing.rb 
..........
Ideas? anyone?

You do not understand how Unix/Linux files work. Files are identified by a "Magic Number", not the file type (that is the Windows way).

When an app creates a file of a specific type, it set the correct "Magic Number". When **you** create a file name using touch, that function has no idea of which of the virtually infinite different file types that you actually want, so it just creates a plain text "Magic Number".

If you want files to have the correct "Magic Number", then use an appropriate app to create them.

---

### Post by karatedog on 2011-06-25
> **dcstar said:**
> You do not understand how Unix/Linux files work. Files are identified by a "Magic Number", not the file type (that is the Windows way).

If you rename a jpeg picture from .jpg to .png, Eye of Gnome will fail to load it, but *feh* will load it. So this is not a 'Linux' way, but entirely an 'application' way.

OTOH, text based source files does not have "Magic number", they are - well - text! And one of their possible state is being empty, which means their size is exactly zero, and that is what *touch* does. The only information these file have: filename and rights.

Linux tools usually happily makes assumption based on the file's extension (yepp, that's what Windows does as well) -> 'application/x-ruby' comes from the extension.

---

### Post by bab1 on 2011-06-25
From the man pages for the command *touch*
```
 [B][COLOR="Red"]
Update  the  access  and modification times of each FILE to the current time.[/COLOR][/B]

A FILE argument that does not exist is created empty.

```

Touch only creates the 0 byte file to compete its real job, which is to update time stamps.  The file name has no content but is linked to a new inode.

---

