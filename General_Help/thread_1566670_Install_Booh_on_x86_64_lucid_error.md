---
title: "Install Booh on x86_64 lucid error"
date: 2010-09-02
forum: General Help
---

### Post by ahbart on 2010-09-02
Hello,
I installed [Booh](http://booh.org/index.html) (the web album generator) on my 64 bit version of Lucid. 
I used this instruction: 
> If your Debian version is not available

Try building from source:

   1. Make sure the following line is somewhere in the APT sources:

      deb-src [http://booh.org/packages/debian/lucid/](http://booh.org/packages/debian/lucid/) ./

      (issue sudo apt-get update if you modified the APT sources for that)
   2. issue sudo apt-get build-dep booh && apt-get --compile source booh
   3. install with sudo dpkg -i booh_*.deb if build was successful

Booh installs well, and I'm able to start the application. But when I try to generate a web album, I get the following error message:

```
/usr/bin/booh-backend:1233:in `+': can't convert nil into String (TypeError)
	from /usr/bin/booh-backend:1233:in `walk_source_dir'
	from /usr/bin/booh-backend:1191:in `each'
	from /usr/bin/booh-backend:1191:in `walk_source_dir'
	from /usr/bin/booh-backend:1171:in `each'
	from /usr/bin/booh-backend:1171:in `walk_source_dir'
	from /usr/bin/booh-backend:834:in `each'
	from /usr/bin/booh-backend:834:in `walk_source_dir'
	from /usr/bin/booh-backend:1649
```

A search on the internet gave me this: [link](http://www.mail-archive.com/booh-discuss@zarb.org/msg00151.html)
But I do not understand what the solution is. 
Could anyone help me with this?

---

