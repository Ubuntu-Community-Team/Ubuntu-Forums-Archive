---
title: "static /etc/motd"
date: 2012-03-12
forum: General Help
---

### Post by theirpuppet on 2012-03-12
I'd really like to have a static /etc/motd. I've checked the docs and google but haven't found the solution yet. Whilst I've seen mention of the tools that update this file upon login, 'update-motd' and 'update-notifier-common', none of these tools are installed:

```

# dpkg -l | grep update
ii  language-pack-en                1:11.10+20120103                        translation updates for language English
ii  update-manager-core             1:0.152.25.8                            manage release upgrades

```

The only thing I can think of is to remove execute bit from everything in /etc/update-motd.d, yet that is not ideal. A package update in the future could easily reset execute bits...

There must be a configurable option somewhere, that will survive package updates. Please advise.

---

### Post by Zill on 2012-03-12
theirpuppet:  I don't use the MOTD myself but a quick web search found [this howto]("http://www.howtogeek.com/104708/how-to-customize-ubuntus-message-of-the-day/").

---

### Post by theirpuppet on 2012-03-12
Thanks, but I am already aware of all this information. Note that the suggestion is to remove the executable bit (chmod -x) which, as I mentioned, is not ideal because it is _not_ future-proof. A package update can easily break that by resetting permissions on those files. There appear to be 3 packages involved:

```

# dpkg -S /etc/update-motd.d/
update-manager-core, base-files, landscape-common: /etc/update-motd.d

```

What I am asking for is a permanent method for disabling this functionality. It's not useful in a production environment to run various scripts to gather information I already know and track via monitoring.

I was thinking their might be an option to pam_motd but the man page only shows a single argument for location of motd file and the source ([https://launchpad.net/ubuntu/+source/pam/1.1.3-2ubuntu2.1](https://launchpad.net/ubuntu/+source/pam/1.1.3-2ubuntu2.1)) confirms this.

```

    for (; argc-- > 0; ++argv) {
        if (!strncmp(*argv,"motd=",5)) {

            motd_path = 5 + *argv;
            if (*motd_path != '\0') {
                D(("set motd path: %s", motd_path));
            } else {
                motd_path = NULL;
                pam_syslog(pamh, LOG_ERR,
                           "motd= specification missing argument - ignored");
            }
        }
        else
            pam_syslog(pamh, LOG_ERR, "unknown option: %s", *argv);
    }

```

But the source also confirms that the pam_motd module is not doing the updating itself. It just opens "motd_path" as readonly, reads it, spits it out, closes fd, exits. More digging to do ...

---

### Post by FruitNuke on 2012-04-01
There are 2 things I had to do to server up a static motd from /etc/motd (on ubuntu 11.04).  Assuming you have edited /etc/motd to have the content you want, do this:

[LIST=1]
[*]Disable pam_motd in the pam configuration for sshd: open /etc/pam.d/ssh in an editor (you'll need to sudo to get write permissions).  Then comment out the line with pam_motd.so in it, so it becomes:> # session    optional     pam_motd.so # [1] and save the file.
[*]Tell sshd to print the motd message: open /etc/ssh/sshd_config in an editor (again using sudo to get write permissions).  Change the line that says: > PrintMotd No to: > PrintMotd Yes  Save the file, then at your shell prompt tell sshd to reload its config by running: > sudo service ssh reload
[/LIST]
Then just establish an SSH connection to test!

What this does is it configures PAM for SSHD to not run the special pam_motd module that Canonical added to Ubuntu, which is what runs the scripts under /etc/update-motd.d when you ssh in.

Hope that helps.

---

