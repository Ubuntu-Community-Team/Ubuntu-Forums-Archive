---
title: "MediaCore Installation problem: python-dev error?"
date: 2010-09-10
forum: General Help
---

### Post by Exxplain on 2010-09-10
Hello,

I'm new to this community and hope that I can find help to solve my big problem due to the Installation of the linux software MediaCore v.0.8.2. ( [http://getmediacore.com/](http://getmediacore.com/) ). 

For your information: Root Server with openSUSE 11.1 - Plesk 9.3. Using putty for interaction with the system. Python, gcc, mysql, python setuptools and virtualenv is installed and should work correctly.

I worked along with the MediaCore v.0.8.2. documentation ( [http://getmediacore.com/docs/install/index.html](http://getmediacore.com/docs/install/index.html) ) and all pre-installations are done. I setup a Python Virtual Environment (Step 1) and go on to Step 2. My server is running python2.6.

When using the command "python2.6 setup.py develop" i get a long error list which ends with:

```
_imaging.c:3138: warning: return type defaults to âintâ
_imaging.c: In function âDL_EXPORTâ:
_imaging.c:3138: error: expected declaration specifiers before âinit_imagingâ
_imaging.c:3149: error: expected â{â at end of input
error: Setup script exited with error: command 'gcc' failed with exit status 1
```

Now I need help to solve this problem. I read that it could be the python-dev? But how can I (re)install it correctly?

Or do you know any other source of the error?

Best regards, XPL :(

---

### Post by d.justins on 2010-12-30
Install python-dev

In Terminal

```
sudo apt-get install python-dev
```

---

