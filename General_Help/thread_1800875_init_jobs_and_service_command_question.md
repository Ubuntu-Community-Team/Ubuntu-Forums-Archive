---
title: "init jobs and service command question"
date: 2011-07-09
forum: General Help
---

### Post by masamunedark on 2011-07-09
Hello all,

I am trying to learn about the upstart init process and everything is going well so far. However, while reading the service command manual it said that it would execute scripts in /etc/init.d directory, so I played around a bit and it seemed to be fine, but I have a script in init.d which starts up sshd daemon called ssh and there was another job configuration file in init jobs directory /etc/init called the same ( ssh.conf).
Now when I start sshd using ( service ssh start ) it runs the init job, not the script in /etc/init.d
even though the man page didn't say anything about that. So, I am wondering if it's configured to act this way in my distro which is ( ubuntu 10.04), and if so then where is the configuration file or how can I configure it ? Or is this simply it's default behavior to first look for a job and then look for the script in /etc/init.d if it can't find the job, but the man page doesn't talk about it. Or am I missing something ?

Thanks all, and execuse my poor English :)

---

