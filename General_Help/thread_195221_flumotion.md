---
title: "flumotion"
date: 2006-06-12
forum: General Help
---

### Post by grooverider on 2006-06-12
Hi there, 
I run the newest ubuntu 6.06 with 2.6.15 kernel, everything is great, downloaded and installed the package flumotion with synaptic, but somehow when i start it from the application menu, i can not choose any option, only go forward until it asks me for a username and password, the default flumotion username and password from the flumotion wiki site, (user/test) don't work, i have no idea how to start the configurator, can someone help me out please, thx a lot

---

### Post by grooverider on 2006-06-13
oki ppl, i was in the fluendo irc chan and the guys have been very helpful, thx again to them, after u installed the ubuntu package of flumotion u actaully only have to follow the instructions from the doc, so don't start flumotion from the applications menu, but open a console and do this:
A FIRST TEST
------------

Once everything is built and installed,
you can try this to start the server:

terminal 1:
  flumotion-manager -v -T tcp /etc/flumotion/managers/default/planet.xml

terminal 2:
  flumotion-worker -v -T tcp -u user -p test

terminal 3:
  flumotion-admin -v

so now the wizard should be in front of u working

---

### Post by R%&amp;92GH&amp; on 2007-01-03
I get this error when starting the worker:

```

marc@BOX:~$ sudo flumotion-worker -v -T tcp -u user -p test
Password:
INFO  [10779]                                  worker            gen 03 17:26:49      Connecting to manager localhost:8642 using TCP (flumotion/worker/main.py:222)
WARN  [10779]                                  worker            gen 03 17:26:49      Shutting down worker because of error: (flumotion/worker/worker.py:113)
WARN  [10779]                                  worker            gen 03 17:26:49      Login failed, reason: [Failure instance: Traceback (failure with no frames): exceptions.AttributeError: 'module' object has no attribute 'implements'
] (flumotion/worker/worker.py:114)
ERROR: Login failed, reason: [Failure instance: Traceback (failure with no frames): exceptions.AttributeError: 'module' object has no attribute 'implements'
]
INFO  [10779]                                  worker            gen 03 17:26:49      All jobs finished, stopping worker (flumotion/worker/main.py:270)

```

anyway, the planet.xml file isn't in /etc/flumotion/managers/default/ by default, have you put it there? 
Must it be edited before doing anythhing else? 
There's any other file that must be edited? 

i've tried lots of combinations and I cannot manage to make it work... :(

---

