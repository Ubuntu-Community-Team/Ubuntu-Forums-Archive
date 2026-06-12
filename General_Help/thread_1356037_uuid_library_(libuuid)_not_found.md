---
title: "uuid library (libuuid) not found???"
date: 2009-12-15
forum: General Help
---

### Post by Gizenshya on 2009-12-15
```
checking for uuid_generate in -luuid... no

configure: error: *** uuid library (libuuid) not found
```


I'm trying to install gparted.  does this mean a missing library?

I found this for qtparted (similar program I guess):

"You may have the following error: configure: error: *** uuid library (libuuid) not found
Uuid is a library included as a part of e2fsprogs. It's required for parted and QtParted. On Ark Linux and similar distributions, install the e2fsprogs-devel package. On other distributions, you may have to install e2fsprogs by compiling sources:
./configure --prefix=/usr ; make ; make install ; make install-libs"

but I don't know what that means.  is there a way toi get that (library?) without compiling it?

Does that library apply to gparted, or just qtparted?  If just qtparted, what is the gparted equiv?

---

### Post by doas777 on 2009-12-15
interesting.

just for diagnostic purposes, 
what do you get from this?
```

sudo ls -l /dev/disk/by-uuid

```

---

### Post by ibuclaw on 2009-12-15
```
sudo apt-get install uuid-dev
```

It's OK, you just don't have the proper developer (-dev) packages installed to build it.

If you run into any other bumps, just say, but you should be able to find the -dev packages easily in the repositories...

ie: libparted - search for **libparted-dev**

Regards
Iain

---

### Post by Gizenshya on 2009-12-15
Well, the problem is I don't have access to the internet on the ubuntu machine.  I have to get to the internet via a win box atm.  sudo apt-get gparted probably would have fixed any problems as they came up, but I had to download the gparted source from the win box.  Now I have to resolve dependencies as I go.

where can I find those programs/files to download from my winbox?  and deb files if possible, source scares me.

btw, if I actually get gparted working it will be the first time I ever actually compiled something from source and eventually got it working :p

---

### Post by Gizenshya on 2009-12-15
is this it?  [http://ns2.canonical.com/search?keywords=libparted1.8-dev](http://ns2.canonical.com/search?keywords=libparted1.8-dev)

that was far harder to find than it should have been...

[http://ns2.canonical.com/jaunty/libparted1.8-dev](http://ns2.canonical.com/jaunty/libparted1.8-dev)

thats the link for jaunty.

which of the versions should I get? orig.tar.gz? ubuntu6.dsc?  ubuntu6.diff.gz?

I don't know what the latter 2 are, so I'm downloading the orig.tzr.gz atm, and await advice :)

---

### Post by ibuclaw on 2009-12-15
> **Gizenshya said:**
> is this it?  [http://ns2.canonical.com/search?keywords=libparted1.8-dev](http://ns2.canonical.com/search?keywords=libparted1.8-dev)

that was far harder to find than it should have been...

[http://ns2.canonical.com/jaunty/libparted1.8-dev](http://ns2.canonical.com/jaunty/libparted1.8-dev)

thats the link for jaunty.

which of the versions should I get? orig.tar.gz? ubuntu6.dsc?  ubuntu6.diff.gz?

I don't know what the latter 2 are, so I'm downloading the orig.tzr.gz atm, and await advice :)

Hmm... you should see a .**deb** file to download there. You will need to download that.

the orig.tar.gz is the original source code.
the diff.gz is the patch for the source to allow building into a debian package.
the dsc is a signed file for authentication of the source + diff.

---

### Post by Gizenshya on 2009-12-15
ok, I looked again and saw the deb and I downloaded and installed it.  Everything went fine.

but then I used ./configure in the gparted folder again... it did a bunch of stuff, but finally returned the exact same error.  :(

what now?

---

### Post by Gizenshya on 2009-12-15
I searched for libuuid stuff on that ubuntu site again and came up with this: [http://ns2.canonical.com/jaunty/amd64/libuuid1/download](http://ns2.canonical.com/jaunty/amd64/libuuid1/download)

from these search results: [http://ns2.canonical.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libuuid](http://ns2.canonical.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libuuid)

I installed it and I still get the same error.   Anyone have an idea what else I can try?

---

### Post by Gizenshya on 2009-12-16
I went back to the ubuntu page for gparted and downloaded the libuuid files directly from the dependency list for gparted... and it STILL won't work.

what gives?  This is incredibly annoying at this point.

---

### Post by ibuclaw on 2009-12-17
> **Gizenshya said:**
> I went back to the ubuntu page for gparted and downloaded the libuuid files directly from the dependency list for gparted... and it STILL won't work.

what gives?  This is incredibly annoying at this point.

Dependencies listed on the page are **Runtime** dependencies.

**Build** dependencies are slightly different.

Requires the following:
 quilt, debhelper, libxml-parser-perl, uuid-dev, parted, pkg-config, gnome-doc-utils, rarian-compat, libgtkmm-2.4-dev, libparted1.8-dev, intltool

And all packages the above depend on, and so forth.

At the end of the day - if you can get some sort of internet connection (even if it is ethernet) - get one setup, as if it is so much easier to run:
```
sudo apt-gt build-dep gparted
```
and let the software take care of everything instead. (Because we are lazy and don't want to download things manually ourselves ;)).

---

