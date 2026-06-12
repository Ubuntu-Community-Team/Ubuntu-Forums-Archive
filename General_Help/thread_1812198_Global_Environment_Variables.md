---
title: "Global Environment Variables?"
date: 2011-07-26
forum: General Help
---

### Post by Wardrop on 2011-07-26
From reading online, it sounds as though the file /etc/environment is the only proper way of defining an environment variable globally. It works most of the time, but it's not always global. One problem I'm currently facing is that the sudo command does not respect environment variables defined in /etc/environment. I have an environment variable set in /etc/environment which determines whether ruby code is run in production or development mode, but if I run any Ruby code under sudo, that environment variable is not set. Running `sudo env` in bash confirms this.

I'm therefore wondering, is there anywhere that's actually truly global for environment variables? My second question, if there's no answer for the first, where do I have to define environment variables for the sudo command to respect them?

NOTE: Using `sudo -i` gets around the problem, but I can't be certain others will include the -i switch.

EDIT: I take that back, sudo -i is not an option as it screws with the current working directory.

Thanks

---

### Post by enimeizoo on 2011-07-26
Well, if your only problem is root, a quick fix would be to edit root's .bashrc .
Root also has a home directory, with config files and so...

That said, I don't know if you can define it globally. I thought /etc files were actually globals. Maybe sudo overwrites env variables for security reasons or something. I dunno.

---

### Post by Wardrop on 2011-07-26
Would it be worth reporting this as a bug do you think?

---

### Post by sisco311 on 2011-07-26
> **Wardrop said:**
> Would it be worth reporting this as a bug do you think?

No. It's a well documented behavior. 

Check out `man sudoers', search for `env_reset', `env_file', `env_keep' and `env_check'.

---

### Post by Wardrop on 2011-07-26
Ok, I used the env_file setting as a line in my sudoers file, as so:

```

Defaults env_file=/etc/environment

```

...which seem to have done the trick. My question is therefore, why isn't this included in the sudoers file by default. I would expect it would be desireable for Ubuntu to ship with this line. Thoughts?

Thanks Sisco311

---

### Post by enimeizoo on 2011-07-27
I'd rather not. I think it is a good thing that my root user is protected from my stupidity.

---

### Post by smallfryfury on 2011-08-13
I was trying to do a similar thing, but ran into a different problem.

```
justin@new-computer:~$ sudo
sudo: /etc/sudoers is mode 0446, should be 0440
sudo: no valid sudoers sources found, quitting
justin@new-computer:~$ 

```

I set the mode to 0446 with sudo. Now I can no longer use sudo.

---

### Post by sisco311 on 2011-08-14
> **smallfryfury said:**
> I was trying to do a similar thing, but ran into a different problem.

```
justin@new-computer:~$ sudo
sudo: /etc/sudoers is mode 0446, should be 0440
sudo: no valid sudoers sources found, quitting
justin@new-computer:~$ 

```

I set the mode to 0446 with sudo. Now I can no longer use sudo.

You can fix the ownership/permissions of the file with the following commands:
```

pkexec chown root:root /etc/sudoers
pkexec chmod 0440 /etc/sudoers

```

---

### Post by smallfryfury on 2011-08-15
Thank you. Global scale disaster: averted

---

