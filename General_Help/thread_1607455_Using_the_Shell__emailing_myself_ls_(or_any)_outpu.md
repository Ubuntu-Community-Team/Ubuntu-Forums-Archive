---
title: "Using the Shell : emailing myself ls (or any) outputs"
date: 2010-10-27
forum: General Help
---

### Post by psymon100 on 2010-10-27
Hi team. 

I have been having some fun with the shell but have become a little lost. I apologise if this is mysteriously posted elsewhere, I promise I did look!

I want to be able to email (myself and others) outputs from various commands etc. Sometimes people wish to know the contents of my music library etc and it's nice to be able to ssh in and email an ls (or similar) output. Here is what I have been doing:
```

ls -R /home/simon/mount/sata0/audio > /tmp/musiclist
mail -s $(date +%Y%m%d) email@domain.com < /tmp/musiclist
```

The date part works perfectly and I receive an email with a subject suiting my preferential YYYYMMDD format. 

_But _what I'd like to figure out is how to get this into a single line of code, my first attempt was:
```

mail -s $(date +%Y%m%d) email@domain.com < $(ls -R /home/simon/mount/sata0/audio)
```
This generates an error, 
-bash: $(ls -R /home/simon/mount/sata0/audio): ambiguous redirect
But if I simply run the code "ls -R /home/simon/mount/sata0/audio" - the output is exactly what I want. 

I was wondering if anyone could point me in the right direction here please, where am I going wrong? Is what I'm trying to do even possible? I do realise that I could use something like this
```

ls -R */directory* > /tmp/file && mail -s $(date +%Y%m%d) email@domain.com < /tmp/file
```
But this is still running two commands and I'd like to figure out how to be 'cleverer'. 

Looking forward to learning from yous guys. 

Regards, Si

---

### Post by steviefordi on 2010-10-27
Try:
```
mail -s $(date +%Y%m%d) email@domain.com << $(ls -R /home/simon/mount/sata0/audio)
```

---

### Post by steviefordi on 2010-10-27
Sorry perhaps more like:

```
mail -s $(date +%Y%m%d) [email]email@domain.com[/email] << EOF
$(ls -R /home/simon/mount/sata0/audio)
EOF
```

It should treat the output of ls into a [here document]("http://en.wikipedia.org/wiki/Here_document").

---

