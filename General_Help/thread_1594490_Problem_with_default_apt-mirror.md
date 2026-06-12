---
title: "Problem with default apt-mirror"
date: 2010-10-12
forum: General Help
---

### Post by Karl1982 on 2010-10-12
I have a Lucid box that I recently set up to netboot install Ubuntu.  What I'm trying to do now is set up an apt mirror so these installations take much less time.  I decided to go with the full mirror instead of a cache because we run a virtual testing environment and I'm likely to need odd packages frequently.  

So, after reading over a couple tutorials, I installed apt-mirror and edited the sources in /etc/apt/mirror.list.  I don't want source files, but my plan is to mirror main, security, and updates for the current and LTS editions, which right now would be lucid and maverick.  I also changed them to what was estimated to be the best mirror.

I wanted to get a feel for the switches in apt-mirror, so I did sudo apt-mirror --help.  This results in the following error:

*apt-mirror: invalid config file specified at /usr/bin/apt-mirror line 122.*

I don't think I caused a problem in /etc/apt/mirror.list, but just in case, I did sudo apt-purge apt-mirror, then reinstalled it and tried again with a default list.  Same error.  So I investigated /usr/bin/apt-mirror, and here is the section around line 122:

```
######################################################################################
## Setting up $config_file variable

$config_file = "/etc/apt/mirror.list";  # Default value
if($_ = shift) {
    die("apt-mirror: invalid config file specified") unless -f $_;
    $config_file = $_;
}

chomp $config_variables{"defaultarch"};


```Line 122 is the one starting with die.  However, it doesn't appear to have the wrong file or anything... I installed all available updates and restarted the server, but it still does this.  Maybe it would function if I removed the conditional statement causing it to fail, but that might just be masking another problem.  I don't like the idea of tampering with it like that anyway.  A default config should work.  Any ideas?

---

### Post by Karl1982 on 2010-10-14
Well... It seems there is no --help switch for apt-mirror.  I think it was taking --help as an alternative config file at runtime.  Run without arguments, it seems to be working fine.  The download will probably be done when I get into the office this morning.

It's odd that the manpage doesn't list a single switch or option.

---

