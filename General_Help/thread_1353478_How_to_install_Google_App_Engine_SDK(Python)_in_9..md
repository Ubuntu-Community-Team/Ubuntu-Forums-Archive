---
title: "How to install Google App Engine SDK(Python) in 9.10?"
date: 2009-12-12
forum: General Help
---

### Post by JoeyF on 2009-12-12
I am following the tut at:

[http://www.digimantra.com/google/google-app-engine/install-run-google-app-engine-linux/](http://www.digimantra.com/google/google-app-engine/install-run-google-app-engine-linux/)

it says:
"After you finish unzipping, you will get a folder google_appengine which has all the necessary files to develop application. To complete the installation and to able to run Google App Engine, we must specify its path definition. You can specify the PATH definition in the terminal only using – export PATH=$PATH:/home/your_user_name/Desktop/google_appengine/

But path specified using export command is valid as long as you are inside the current terminal window. That means as soon as you close the window, the path specified becomes invalid. To specify the path in the system, you have to edit the /home/your_user_name/.profile and specify the path there."

So i went to my Username folder but i don't see a .profile.

Help?

Thanks.
:)

---

### Post by mbeach on 2009-12-12
let's say your home directory is:
/home/joeyf/

and you've now got a folder with google app engine in
/home/joeyf/google_appengine

and your application that you are writing with the app.yaml and what not in 
/home/joeyf/gapps/myapp

from the terminal try something like```

cd ~
./google_appengine/dev_appserver.py ./gapps/myapp

```

edit:
and to answer your question, perhaps putting the export command in ~/.bashrc instead of profile might work for you. Put it towards the end of that file and you'll probably be okay.```
gedit ~/.bashrc
```
you'll need to log out of that terminal session and start a new one (or type 'bash' at the prompt).

edit 2:
also, if you are wanting to put it in .profile, I bet you do have that file, just are not seeing it.
```
gedit ~/.profile
```

---

### Post by mbeach on 2009-12-12
also, you are likely going to want to install python2.5 as well as the version you currently have (there are no real issues in having both).

to install python2.5```
sudo apt-get install python2.5
```

after installed, you'll want to edit your 
/google_appengine/dev_appserver.py
and
/google_appengine/appcfg.py

first lines to look like:
#!/usr/bin/env python2.5

If you have problems editing those two files, right click on them, select 'properties' then go to the permissions tab. Make sure you as the owner can read and write. After you edit, you may want to put that permission back to read-only.

---

### Post by JoeyF on 2009-12-12
Ok, One last thing. What do i type in .profile to specify the path? is it export PATH=$PATH:/home/your_user_name/Desktop/google_appengine/?

Thanks,

---

### Post by mbeach on 2009-12-12
I would say you really don't need to do it at all, as long as you call dev_appserver.py with its full path.

However, I'd say you'd be safe with:
export PATH=$PATH:/home/yourusername/google_appengine

It should be obvious that you need to use the actual path to where ever you place google_appengine.

reference:
[http://www.linuxheadquarters.com/howto/basic/path.shtml](http://www.linuxheadquarters.com/howto/basic/path.shtml)

edit:
might want to take a read of:
[http://ubuntuforums.org/showpost.php?p=2590722&postcount=3](http://ubuntuforums.org/showpost.php?p=2590722&postcount=3)

---

### Post by JoeyF on 2009-12-12
So i just add the path to my .bashrc? and then add #!/usr/bin/env python2.5 to my python files?


Sorry, I'm a noob.

Thanks.

---

### Post by mbeach on 2009-12-12
sure, give that a whirl.

I personally don't bother with adding it to the path, as it is unessesary. As long as you kick off the server with something like
./google_appengine/dev_appengine.py ./path/to/my/app
it will work fine.

There are other ways to get the app engine files to use python 2.5 but I find amending the first line as shown is the easiest (after you have installed python 2.5)

try to run it - if you get errors, report back here and we'll sort it out.

---

### Post by Yrrepperry on 2010-09-15
How can you confirm that 
#!/usr/bin/env python2.5
is working?

I still get errors in the Google app engine tutorial I am trying to run:
(on ubuntu 10.04)

Traceback (most recent call last):   File "/home/perry/google_appengine/google/appengine/ext/webapp/__init__.py", line 511, in __call__     handler.get(*groups)   File "/home/perry/helloworld/helloworld.py", line 32, in get     self.response.out.write(template.render(path, template_values)) NameError: global name 'template_values' is not defined

---

### Post by mbeach on 2010-09-29
Can you paste your helloworld.py file here (in code blocks). I suspect that your template_values variable is not set by the time you call it on line 32.

---

