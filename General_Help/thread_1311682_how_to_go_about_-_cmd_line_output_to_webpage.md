---
title: "how to go about - cmd line output to webpage"
date: 2009-11-02
forum: General Help
---

### Post by marbour on 2009-11-02
Hi dear community.

I have a ubuntu server that works just fine the way I like it...

I would like to add this: instead of logging in via ssh and starting bwm-ng (real time bandwidth monitoring to console... a little like top for processes), I would like the results to be put on a webpage at some intervals (depending on resource usage... from 1 to 5 seconds)

Is there a known way of doing this easily? via a package for example

Any pointers into a solution will be very much appreciated.

Regards.

Marc

---

### Post by prem1er on 2009-11-02
You could just write a bash process to do this. Just have the process run on the interval of your choice and then redirect the results to an html file. If you are running a webserver you could browse to that file and you will be able to view your results. I'm not aware of a process that would do this for you automatically, but maybe someone knows of a web service used to monitor system information?

---

### Post by dcstar on 2009-11-02
> **prem1er said:**
> You could just write a bash process to do this. Just have the process run on the interval of your choice and then redirect the results to an html file. If you are running a webserver you could browse to that file and you will be able to view your results. I'm not aware of a process that would do this for you automatically, but maybe someone knows of a web service used to monitor system information?

Web pages can be easily set up to auto-refresh at any interval, all of this is basic HTML stuff and there are literally thousands of resources already out there on how to do it - all at the end of a web search.

---

### Post by marbour on 2009-11-03
Thanks prem1er.

Good answer. But bash scripts are ran every minute via cron at the minimum. Am I correct?

What should/could I do to get updates every 2-5 seconds?

As suggested by dcstar, the refreshing of the webpage doesn't "really" occur in the browser if the originating html (or the like) file has not been re-written.

I did a lot of searching but with the words I am using (see thread title) I do not have ANY success at all finding something.

Any others with suggestions? Or ideas?

Best regards.

Marc

---

### Post by szaboz on 2009-11-03
hi;

mabe have a look in the man pages or here ::

[http://www.ubuntugeek.com/images/bandwidth/bwm-ngmanpage.htm](http://www.ubuntugeek.com/images/bandwidth/bwm-ngmanpage.htm)

that is an option to select in bwm-ng

---

### Post by marbour on 2009-11-03
Wow!

I must admit my fault.

I had not read that up to the bottom.

So refreshing not having been burnt.

Thanks a lot for pointing it out.

Marc

---

### Post by marbour on 2009-11-03
To all those wishing to do the same... I did this to get this running...

After bwm-ng is installed and working via command line...

create a file called /etc/cron.hourly/bwm and put this in...
> #!/bin/bash
if ps -ef | grep "bwm-ng" | grep -v grep >/dev/null
then
echo "bwm-ng script running"
else
bwm-ng -o html -R 1 -H 1 -t 1000 -D 1 -F /your/web/directory/bw.html
fi 


Then make the file executable and wait for the next hour... It'll start automatically or get started if not.

Then, you access page [http://yourdomain/bw.html](http://yourdomain/bw.html).

Voilà.

Marc

---

