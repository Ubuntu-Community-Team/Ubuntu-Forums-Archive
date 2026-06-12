---
title: "Command line programs to download subtitles?"
date: 2012-10-07
forum: General Help
---

### Post by honeybear on 2012-10-07
Hi,

It exists submarine. Submarine is a command-line program for searching and downloading the right subtitles for movies.
[https://github.com/blazt/submarine](https://github.com/blazt/submarine)

would you know others prg that use bash and curl/wget simply?
(or python)

thx

---

### Post by honeybear on 2012-10-07
[https://github.com/Diaoul/subliminal/zipball/develop](https://github.com/Diaoul/subliminal/zipball/develop)

there is too this one. The dependencies are : 

python
python-setuptools 


but how to run it wihtout installing it ?

python ...?

thanks

---

### Post by cipherboy_loc on 2012-10-07
Correction, the full dependencies are as follows:
> 
Optional:
lxml
Required: 
beautifulsoup4>=4.0
guessit>=0.4.1
requests
enzyme>=0.1
html5lib
 
(from optional-requirements.txt and requirements.txt)

In the /scripts/ directorory (relative to the path of the source), you will see a file called subliminal. If you can't just run it there, as is, copy it to the /subliminal/ directory to fix the import errors.


Thanks,
Cipherboy

---

### Post by honeybear on 2012-10-08
> **cipherboy_loc said:**
> Correction, the full dependencies are as follows:
 
(from optional-requirements.txt and requirements.txt)

In the /scripts/ directorory (relative to the path of the source), you will see a file called subliminal. If you can't just run it there, as is, copy it to the /subliminal/ directory to fix the import errors.


Thanks,
Cipherboy

Thanks.
It is pretty much, isnt it?

Could not be based on a minimum of packages as youtube-dl ?

---

