---
title: "Every Single process is sleeping!"
date: 2011-07-19
forum: General Help
---

### Post by grindboy on 2011-07-19
Hi Guys,

I'm running 11.04 with the 2.6.38-10-generic-pae kernel. Recently OpenShot stopped launching. When checking in system monitor I noticed that all of the process (every single last one of them) is sleeping.

They are all marked as either futex_wait_queue_me or poll_schedual_timeout.

My system specs are listed in my signature and I can provide any logfiles you need as long as you can tell me where to find them.

I've done a lot of Googling of the subject (since I don't like bothering you fine folks with things I can figure out myself) but this issue has been cropping up since before 8.04 and I haven't found a single post relating to it marked as solved.

I understand that it is a issue with the kernel which the devs have been planning on fixing since 2009.

Any help would be greatly appreciated I'd rather not have to reinstall ubuntu again but my data is all on a separate drive so doing so would be a simple task.

Many Thanks

Michael

---

### Post by Mr Nemo on 2011-07-19
Provide a few screenshots if you have them available. I don't think there's anything wrong with your system, but a few screenshots of your system monitor would be helpful.

---

### Post by grindboy on 2011-07-19
Here you go:

---

### Post by Mr Nemo on 2011-07-19
That seems pretty normal to me. All processes are usually sleeping unless they are being used by the system. As long as your system isn't acting funny, it's ok.

---

### Post by grindboy on 2011-07-19
Well that's just it. OpenShot a video editing program I use. Refuses to launch. It's process starts as futex_wait_queue_me and the program never opens.

I tried reinstalling it through the software centre. I might try a complete removal and reinstall through synaptic next unless you have another suggestion.

---

### Post by Frogs Hair on 2011-07-19
Try this command below in the terminal to see running processes . I don't know why the system monitor is reporting every process as sleeping.
```
top
```

---

### Post by grindboy on 2011-07-19
OK doing a complete removal and reinstall of openshot hasn't helped.

Top outputs: 

```
Tasks: 183 total,   1 running, 181 sleeping,   0 stopped,   1 zombie
```

along with the big list of tasks

---

### Post by dino99 on 2011-07-19
you might search about a missing driver (gstreamer ...), watch logs to find usefull errors.

all normal about process sleeping: dynamic ram scaling

---

### Post by regala on 2011-07-19
when you run OpenShot thru a terminal, what does the terminal outputs to the screen ?

br,

---

### Post by grindboy on 2011-07-19
Why didn't I think of running openshot from terminal? I get the following:

```
------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.3.1)
--------------------------------
Process no longer exists: 2140.  Creating new pid lock file.

------------------------- ERROR 2 ------------------------------
Failed to import 'from openshot.openshot import main'
Error Message: 'NoneType' object has no attribute 'set_cursor'
----------------------------------------------------------------

OpenShot has failed to import some of the Python files or libraries 
required for our application to run.  Here are some trouble shooting
tips:

Tip 1) Check if MLT can be successfully imported in Python.  Run the 
 following commands, and see if any errors are displayed.  If you get 
 an error, you need to investigate the correct way to install MLT.
 NOTE:  Do not type the $ or >> characters in the examples below.

       $ python
       >> import mlt
       >> mlt.Factory().init()

Tip 2) If MLT is working from the first example, then the next tip is 
 to look at the above error messages very closely, and google for more 
 help.  It's likely the problem is already reported, and maybe there is
 a simple work-around.  Also, you can search for bugs or report a new 
 bug at https://bugs.launchpad.net/openshot.  Good luck!

```

I'll probably post it on the openshot forums unless one of you gentlemen know of a solution.

I ran the python commands, the first executed without problems the second printed:
```
<mlt.Repository; proxy of <Swig Object of type 'Mlt::Repository *' at 0xb72dea58> >

```

Any thoughts?

---

### Post by incognita on 2011-07-19
> **grindboy said:**
> Why didn't I think of running openshot from terminal? I get the following:

```
------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.3.1)
--------------------------------
Process no longer exists: 2140.  Creating new pid lock file.

------------------------- ERROR 2 ------------------------------
Failed to import 'from openshot.openshot import main'
Error Message: 'NoneType' object has no attribute 'set_cursor'
----------------------------------------------------------------

OpenShot has failed to import some of the Python files or libraries 
required for our application to run.  Here are some trouble shooting
tips:

Tip 1) Check if MLT can be successfully imported in Python.  Run the 
 following commands, and see if any errors are displayed.  If you get 
 an error, you need to investigate the correct way to install MLT.
 NOTE:  Do not type the $ or >> characters in the examples below.

       $ python
       >> import mlt
       >> mlt.Factory().init()

Tip 2) If MLT is working from the first example, then the next tip is 
 to look at the above error messages very closely, and google for more 
 help.  It's likely the problem is already reported, and maybe there is
 a simple work-around.  Also, you can search for bugs or report a new 
 bug at https://bugs.launchpad.net/openshot.  Good luck!

```

I'll probably post it on the openshot forums unless one of you gentlemen know of a solution.

I ran the python commands, the first executed without problems the second printed:
```
<mlt.Repository; proxy of <Swig Object of type 'Mlt::Repository *' at 0xb72dea58> >

```

Any thoughts?

Is Python 2 installed in your system? If not - 
```
 apt-get install python-dev
```

If yes, check if the python path is set properly: 
```
$ echo $PYTHONPATH
```

---

### Post by Mr Nemo on 2011-07-19
+1 for terminals. They've solved a lot of my problems.

---

### Post by roololing on 2011-07-19
Yeah, when you open the System Monitor every process is usually asleep except, of course, for the System Monitor. That's perfectly normal and probably has nothing to do with your problem.

---

### Post by grindboy on 2011-07-26
Hey incognita.

Sorry for not getting back to you sooner. I've installed Python 2 but running echo $PYTHONPATH just gives me blank line.

Thanks

---

### Post by incognita on 2011-07-26
> **grindboy said:**
> Hey incognita.

Sorry for not getting back to you sooner. I've installed Python 2 but running echo $PYTHONPATH just gives me blank line.

Thanks

Hi! That would mean that your python path has not been set properly. Try this :

```
export PYTHONPATH=$PYTHONPATH:/usr/lib/python2.6/site-package/
```

I do not know exactly which version of python you are using. Just replace the correct version for 2.6

Do let me know what happens after that!

---

### Post by grindboy on 2011-07-27
OK so, it's python 2.7 (FWIW) ran the command fine. Echo now works but openshot still fails to launch and prints the same messages. I tried the mlt stuff again and that also errored out with the same message as before.

Cheers

---

### Post by boonybouncer on 2011-11-07
I'm having the same issue with openshot, did you ever find a solution?

---

### Post by grindboy on 2011-11-08
For me the problem fixed itself when I upgraded to 11.10. Sorry I can't be of more help.

---

### Post by boonybouncer on 2011-11-08
No problem, I'm sure it will be fixed by 12.04. Pitivi for now. Thanks, anyways.

---

### Post by deejaylight on 2012-06-14
Hello everyone!
I have the same problem with skype and ubuntu 12.04.
Skype each 30min goes in the futex_wait_queue_me and I cannot do anything, my contacts say that I'm offline. And I have to kill the process and reopen it.

Does anyone know what may be the problem?
Or how to trobleshoot that?

I would appreciate your help!
Thanks!

---

### Post by deejaylight on 2012-06-21
Skype 4 for linux seems that solved the problem

---

