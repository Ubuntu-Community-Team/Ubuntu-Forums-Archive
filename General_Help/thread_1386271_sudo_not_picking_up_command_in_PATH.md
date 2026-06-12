---
title: "sudo not picking up command in PATH"
date: 2010-01-20
forum: General Help
---

### Post by dasil003 on 2010-01-20
On my Ubuntu server I'm running into an issue that I've never seen before even though I've been using Linux for many years.  Basically sudo is not finding a command located in my path.  Here is a transcript illustrating the problem.  Any ideas?

```
prg ~: echo $PATH
/opt/ruby/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
prg ~: sudo echo $PATH
/opt/ruby/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
prg ~: which ruby
/opt/ruby/bin/ruby
prg ~: sudo which ruby
prg ~: 

```

---

### Post by Cabs21 on 2010-01-20
> **dasil003 said:**
> On my Ubuntu server I'm running into an issue that I've never seen before even though I've been using Linux for many years.  Basically sudo is not finding a command located in my path.  Here is a transcript illustrating the problem.  Any ideas?

```
prg ~: echo $PATH
/opt/ruby/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
prg ~: sudo echo $PATH
/opt/ruby/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
prg ~: which ruby
/opt/ruby/bin/ruby
prg ~: sudo which ruby
prg ~: 

```

I dont see an error or issue.  Is it that nothing seems to happen after you type ```
sudo which ruby
```
also if ruby is not in your current directory it will not find it.  I looks like you are trying to run something in your home folder correct?

---

### Post by dasil003 on 2010-01-20
> **Cabs21 said:**
> I dont see an error or issue.  Is it that nothing seems to happen after you type ```
sudo which ruby
```

yes, that's the issue.  /opt/ruby/bin is clearly in the path both as the logged-in user and also when running a command as sudo.  The question then, is why ruby is found only when running without sudo.

> **Cabs21 said:**
> also if ruby is not in your current directory it will not find it.  I looks like you are trying to run something in your home folder correct?

Where would you get that idea?  The $PATH is basic Linux functionality.  Why are you saying you need to be in the same directory to run something, that just doesn't even make the first bit of sense.

---

### Post by VCoolio on 2010-01-20
You can set root path in /etc/environment.

Reason why sudo echo $PATH seemed to find it is because it copies user environment. See the difference if you do:

sudo -i
echo $PATH

and exit; now:
sudo -s
echo $PATH

with sudo -i you get root environment; with sudo -s user environment. Rather, sudo -i executes as root; sudo -s executes as user with superuser permissions.

---

### Post by dasil003 on 2010-01-20
> **VCoolio said:**
> You can set root path in /etc/environment.

Thanks for the reply, however root user settings are not in play here.  As a matter of fact the same path *is* set in /etc/environment, and if I do sudo su to login as root I can use the ruby executable no problem.

So to summarize.  As a user I can access the ruby executable, and as root I can also access it, however when running with plain sudo I can not.

**How is it possible that `which ruby` does not find the exe even though it is in the$PATH?**

---

### Post by VCoolio on 2010-01-20
I don't know, but maybe it has to do with the way things are installed; if I do 'sudo which ruby' it has output /usr/bin/ruby; but when I do that on something I installed in /opt I get the same issue as you are experiencing.

---

### Post by bodhi.zazen on 2010-01-20
> **dasil003 said:**
> **How is it possible that `which ruby` does not find the exe even though it is in the$PATH?**

See if [this discussion](http://stackoverflow.com/questions/257616/sudo-changes-path-why) helps your understanding =)

---

### Post by dasil003 on 2010-01-20
Wonderful link, thank you very much.

---

