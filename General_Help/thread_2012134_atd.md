---
title: "atd"
date: 2012-06-28
forum: General Help
---

### Post by chemjeff on 2012-06-28
How can I configure atd to work on an SMP computer?  I can't seem to find any configuration files for it.

---

### Post by matt_symes on 2012-06-28
Hi

> **chemjeff said:**
> How can I configure atd to work on an SMP computer?  I can't seem to find any configuration files for it.

Shouldn't it just run on an SMP machine ?

This is from 

```
man atd
```

> -l      Specifies  a  limiting  load factor, over which batch jobs should not be run, instead of the compile-time choice of 1.5.  For an SMP system with n CPUs, you will probably want to set this higher than n-1.

To me, this suggests it should.

Also from the manual

> FILES
       /var/spool/cron/atjobs The directory for storing jobs; this should be mode 700, owner daemon.

       /var/spool/cron/atspool The directory for storing output; this should be mode 700, owner daemon.

       /etc/at.allow, /etc/at.deny determine who can use the at system.

Are you having problems using the at command ?

Kind regards

---

### Post by chemjeff on 2012-07-04
> **matt_symes said:**
> Hi



Shouldn't it just run on an SMP machine ?

This is from 

```
man atd
```



To me, this suggests it should.

Also from the manual



Are you having problems using the at command ?

Kind regards



But I don't know how to pass the option to atd.  It just starts up on its own.

But now I am not sure if I really want to use atd.  What I really want to be able to do is to be able to run batch jobs where I can submit a bunch of jobs to a queue, some of them parallel jobs, and they will run when the appropriate number of cores become available.  what is the best way to do this with Ubuntu?

---

### Post by matt_symes on 2012-07-04
Hi

To control atd you use the at command. I think you may be looking for a mixture of at and the batch command.

Here is a link for you

[http://manpages.ubuntu.com/manpages/lucid/man1/at.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/at.1.html)

Check out the section for batch.

> **batch**   
executes commands when system  load  levels  permit;  in  other                words,  when  the  load  average  drops below 1.5, or the value                specified in the invocation of **atd**.Kind regards

---

### Post by chemjeff on 2012-07-04
> **matt_symes said:**
> Hi

To control atd you use the at command. I think you may be looking for a mixture of at and the batch command.

Here is a link for you

[http://manpages.ubuntu.com/manpages/lucid/man1/at.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/at.1.html)

Check out the section for batch.

Kind regards


"executes commands when system load levels permit; in other words, when the load average drops below 1.5, or the value specified in the invocation of atd. "

This is the problem here, how can I change this load value of 1.5 when atd is invoked?  I know about the -l option but I can't figure out how to pass the -l option arguments to atd when it just starts up automatically.

Also, will batch work for parallel jobs?

---

### Post by matt_symes on 2012-07-04
Hi

> executes commands when system load levels permit; in other words, when  the load average drops below 1.5,*or the value specified in the  invocation of atd*.You could edit the upstart file that spawns (invocates) atd

Take a look in 

```
/etc/init/atd.conf
```Look for the line that says

```
exec atd
```and add your parameters after atd.

That should work.

I also cannot find a config file for atd so this may be the only way to do it. If there is a config file for atd then i am sure someone will point this out.

You may need to reboot your PC if restarting atd does not run from the init file.

> Also, will batch work for parallel jobs?Not sure. Try it and post back to help other users :)

Kind regards

---

