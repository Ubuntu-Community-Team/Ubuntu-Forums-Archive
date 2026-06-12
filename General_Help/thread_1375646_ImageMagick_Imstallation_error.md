---
title: "ImageMagick Imstallation error"
date: 2010-01-08
forum: General Help
---

### Post by tejasd on 2010-01-08
Hi all..
I am getting error like
"/usr/lib/ruby/1.8/i486-linux/RMagick2.so: This installation of RMagick was configured with ImageMagick 6.5.1 but ImageMagick 6.5.8-10 is in use. (RuntimeError)
"

So, I am trying to install ImageMagick 6.5.1. But it gives me error like 
"ERROR: Can't create '/usr/local/man/man3"

And I am using Ubuntu 9.10

Any solutions....

---

### Post by gsmanners on 2010-01-08
Are you installing from the repos?

```
apt-cache -n search magick
```

---

### Post by tejasd on 2010-01-11
Thanks for your reply...

I have successfully installed the ImageMagick 6.5.1-0. 
But I am still getting the error like 
"/usr/lib/ruby/1.8/i486-linux/RMagick2.so: This installation of RMagick was configured with ImageMagick 6.5.1 but ImageMagick 6.5.8-10 is in use. (RuntimeError)"

Please help me out.....

---

### Post by keber on 2010-03-31
quite old, but i had a similar problem with an Ubuntu server.

```
sudo apt-get install librmagick-ruby1.8 
```

did the trick for me. Hope this helps anyone.

---

