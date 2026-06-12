---
title: "Gwibber not showing the general timelines"
date: 2010-04-30
forum: General Help
---

### Post by bashphoenux on 2010-04-30
I installed ubuntu lucid lynx and setup my twitter and identi.ca account on the social web browser 
but i notice that I am only able to replies i.e @myname: messages and am unable to see my status timelines as well as my friends and ....
what is the problem ???? have I missed something????

---

### Post by protagonistmohit on 2010-05-02
I too am facing the same issue , I want to start a new thread but I am not able to find any button to click on to start a new thread regarding the same issue.
Gwibber isn't updating new time lines on UBUNTU 10.04, I can't even write messages or tweets.I think due to overload of issues - the "new thread" button is disabled on the forum.

When I start Gwibber in terminal & press [SIZE=4][COLOR=Red]" CTRL + R "[/COLOR][/SIZE] , then in terminal ( I get the message - like -[COLOR=Red][B] [SIZE=4]

[** (gwibber:2940): CRITICAL **: murrine_style_draw_box: assertion `width >= -1' failed][/SIZE][/B][/COLOR]

---

### Post by bashphoenux on 2010-05-03
well I don't get that error but the main timelines aren't displayed !!
that is the status message of mine and my friends ...etc
in KDE environment there is a client called choqok, really nice :)
but unfortunately there is no substitute for that in gnome :( besides GWIBBER AFAIK!

---

### Post by spitfire23bc on 2010-05-10
Same here. I don't get any error messages, but I can't see my timeline in *any* client I've tried (Gwibber, Twitux and Pino). I am also unable to post new tweets from them.

Flickr in Gwibber works fine, so [s]I am sure it is[/s] it may be a problem with Twitter integration in Lucid, rather than just a Gwibber problem.

In Gwibber, I am able to use the Twitter search function; and Pino detects and downloads my Twitter avatar, so they are connecting to Twitter in some form.

Running ```
gwibber-service -o -d
``` gives:

```
Updating...
Gwibber Dispatcher: DEBUG    Setting up monitors
Gwibber Dispatcher: DEBUG    Monitors are up
Gwibber Dispatcher: INFO     Gwibber Service is reloading account credentials
Gwibber Dispatcher: DEBUG    Refresh interval is set to 5
Gwibber Dispatcher: DEBUG    Account deleted: twitter-spitfire23bc
Gwibber Dispatcher: INFO     Gwibber Service is reloading account credentials
Gwibber Dispatcher: DEBUG    Account changed: twitter-spitfire23bc
Gwibber Dispatcher: DEBUG    ** Starting Single Operation **
Gwibber Dispatcher: DEBUG    <twitter:receive> Performing operation
Gwibber Dispatcher: DEBUG    <twitter:responses> Performing operation
Gwibber Dispatcher: DEBUG    <twitter:responses> Finished operation
Gwibber Dispatcher: DEBUG    <twitter:private> Performing operation
Gwibber Dispatcher: DEBUG    <twitter:receive> Finished operation
Gwibber Dispatcher: DEBUG    Refresh interval is set to 5
Gwibber Dispatcher: DEBUG    ** Starting Refresh - Mon May 10 17:23:23 2010 **
Gwibber Dispatcher: DEBUG    <twitter:receive> Performing operation
Gwibber Dispatcher: DEBUG    <twitter:responses> Performing operation
Gwibber Dispatcher: DEBUG    <twitter:private> Finished operation
Gwibber Dispatcher: INFO     Loading complete: 1 - ['Success', 'Success', 'Success']

```

No errors whatsoever, but I don't have a timeline.

---

### Post by bashphoenux on 2010-05-10
mate if you really want a nice client try qwit,
its really nice has support for identi.ca and twitter and others would work if you know how to set it up. QWIT pretty much does my job cause mostly I use identi.ca or twitter *thumbs up* for qwit
I am surprised there is still no update from the Ubuntu side...

---

### Post by spitfire23bc on 2010-05-10
Well, after fiddling around with it, I now have it all working properly. I have no idea what I've done to get it to work, but it does, so I'm not complaining!


> **bashphoenux said:**
> mate if you really want a nice client try qwit,
its really nice has support for identi.ca and twitter and others would work if you know how to set it up. QWIT pretty much does my job cause mostly I use identi.ca or twitter *thumbs up* for qwit
I am surprised there is still no update from the Ubuntu side...

Thanks, Qwit looks pretty nice, but I'm sticking with Gwibber for now.

---

### Post by x-shaney-x on 2010-05-10
I have spent much of my free time today trawling through hundreds of bug reports about various problems with gwibber and I am yet to see any kind of response to suggest they are doing anything about it so I'm not honestly expecting it working this side of Meerkat.

---

### Post by asn_knight on 2010-05-12
> **spitfire23bc said:**
> Well, after fiddling around with it, I now have it all working properly. I have no idea what I've done to get it to work, but it does, so I'm not complaining!


HOW DID YOU DO IT? If you dont know how, What where you trying to do?

---

### Post by mordoc on 2010-05-12
I too would love to know how you turned the general timeline on, it is driving me nuts...

---

### Post by flightless bird on 2010-05-15
What's even odder is I installed it at work and it worked fine, but when I did a fresh install on my home laptop, which already had a gwibber installation, I got no timelines. Very strange.

---

### Post by swappa on 2010-05-20
Have the same problem. Gwibber is simply not updating at all.
This is what I get;


Xlib:  extension "RANDR" missing on display ":0.0".
Updating...
Gwibber Dispatcher: DEBUG    Setting up monitors
Gwibber Dispatcher: DEBUG    Monitors are up
Gwibber Dispatcher: INFO     Gwibber Service is reloading account credentials
Gwibber Dispatcher: DEBUG    Refresh interval is set to 5
Gwibber Dispatcher: DEBUG    ** Starting Refresh - Thu May 20 21:44:44 2010 **
Gwibber Dispatcher: DEBUG    <twitter:responses> Performing operation
Gwibber Dispatcher: DEBUG    <twitter:receive> Performing operation
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (6, 'name lookup timed out')
Gwibber Dispatcher: ERROR    Failed to communicate with [https://twitter.com/statuses/mentions.json?count=200](https://twitter.com/statuses/mentions.json?count=200)
Gwibber Dispatcher: ERROR    Failed to parse the response, error was: No JSON object could be decoded
Gwibber Dispatcher: ERROR    <twitter:responses> Operation failed
Gwibber Dispatcher: DEBUG    Traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/dispatcher.py", line 81, in perform_operation
    message_data = PROTOCOLS[account["protocol"]].Client(account)(opname, **args)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/twitter.py", line 146, in __call__
    return getattr(self, opname)(**args)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/twitter.py", line 155, in responses
    return self._get("statuses/mentions.json", count=count, since_id=since)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/twitter.py", line 136, in _get
    if data.has_key("error"):
AttributeError: 'str' object has no attribute 'has_key'

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/network.py", line 32, in __init__
    self.curl.perform()
error: (6, 'name lookup timed out')
Gwibber Dispatcher: ERROR    Failed to communicate with [https://twitter.com/statuses/home_timeline.json?count=200](https://twitter.com/statuses/home_timeline.json?count=200)
Gwibber Dispatcher: ERROR    Failed to parse the response, error was: No JSON object could be decoded
Gwibber Dispatcher: ERROR    <twitter:receive> Operation failed
Gwibber Dispatcher: DEBUG    Traceback:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/dispatcher.py", line 81, in perform_operation
    message_data = PROTOCOLS[account["protocol"]].Client(account)(opname, **args)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/twitter.py", line 146, in __call__
    return getattr(self, opname)(**args)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/twitter.py", line 149, in receive
    return self._get("statuses/home_timeline.json", count=count, since_id=since)
  File "/usr/lib/python2.6/dist-packages/gwibber/microblog/twitter.py", line 136, in _get
    if data.has_key("error"):
AttributeError: 'str' object has no attribute 'has_key'

---

### Post by Egor Zvukov on 2010-05-25
Anyone got the answer?

---

### Post by x-shaney-x on 2010-05-25
Well I found an answer that works for me:
Just stick to using facebook in a web browser (or prism-facebook in the repos).

I'm afraid I find gwibber so utterly useless and pointless that I'm not even going to bother trying with it anymore.
It didn't work properly in the Lucid alpha, still hasn't worked through the betas and RC and now almost a month into the release and it still doesn't look like ever getting sorted.

I have been very pleasantly suprised by Lucid and think it's great but gwibber has been a very big disappointment.
Especially for something touted as a major feature.

---

### Post by yafes on 2010-06-11
probably one gwibber instance still hang. kill it (ps -ef |grep gwibber) and try again.

---

### Post by delcastanher on 2010-06-29
It worked for me:

Go to System -> Administration -> Language Support.
In the Language & Test window keep click on Apply System-Wide. Go to the  Text Tab and click on Apply System-Wide.

Source: [http://digitizor.com/2010/05/23/how-to-fix-gwibber-bug-of-not-updating-the-twitter-timeline/](http://digitizor.com/2010/05/23/how-to-fix-gwibber-bug-of-not-updating-the-twitter-timeline/)

---

### Post by MickSulley on 2011-01-25
Anyone any idea how to fix this?  I stated using Gwibber a few weeks back for Facebook and Twitter and was very impressed.  A couple of days ago the Twitter timeline stopped.  I have tried the language setting fix and killing the processes, neither have made any difference.

Ideas?????

---

