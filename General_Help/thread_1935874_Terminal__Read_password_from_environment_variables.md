---
title: "Terminal : Read password from environment variables . . ."
date: 2012-03-05
forum: General Help
---

### Post by haseebifkaar on 2012-03-05
Hy,

I was wondering whether there is anyway we can have the "sudo, su or any" command read the required password from an environment variable that we set ourselves right before we execute it, either in a script or in a sequence of commands in the terminal.

And also, while we are on it, can we have the password read from a file(of our choosing or some predefined system file).

Thanks in advance.

Regards

---

### Post by lechien73 on 2012-03-05
Hi & welcome to the forums,

You can have the password set as an environment variable and passed to sudo, although this is very insecure since the password would be stored as plain text.

If you're on a home network and not too bothered about that, then you could achieve it with a script like the following:

```
#!/bin/bash

PW = "TestPassword"
echo $PW | sudo -S [command]
```

Replace [command] with whatever command you want to have executed as su

You could read this from a file as follows, where ~/passwordfile contains a single line with the sudo password in it:

```
#!/bin/bash

while read pwline
do
  PW="$(echo $pwline)"
done < ~/passwordfile

echo $PW | sudo -S [command]
```

As I said, I'm not sure why you'd want to do it - and certainly don't use it in a production environment!

---

### Post by Khayyam on 2012-03-05
> **haseebifkaar said:**
> I was wondering whether there is anyway we can have the "sudo, su or any" command read the required password from an environment variable that we set ourselves right before we execute it, either in a script or in a sequence of commands in the terminal.

Sudo (since 2008, or thereabouts) doesn't respect environment variables, though you can define them after the fact (ie: as part of the subsequent command). This doesn't help but in your case but I wonder why you don't simply use sudoers and define the user/command that you want to be passwordless.

Similarly for 'su' ... no stdin other than the tty.

mysql, ldap{add|modify} will accept password from the environment, but they have --password= switches.

> **haseebifkaar said:**
> And also, while we are on it, can we have the password read from a file (of our choosing or some predefined system file).

Next you'll want that its read via your vcam pointing at a post-it note .. heh .. no, but again the use of sudoers is enough that certain users can run certain commands without being prompted for a password.  

HTH ... khay

---

### Post by Khayyam on 2012-03-05
> **lechien73 said:**
> You can have the password set as an environment variable and passed to sudo, although this is very insecure since the password would be stored as plain text.

Odd, becuase I remember the whole bruhaha on the sudo list when they were changing to 'no variables', even 'RSYNC_PROXY' was to be nulled.

Still, sudoers is recommended.

best ... khay

---

### Post by haseebifkaar on 2012-03-05
Thank you for a quick reply.

The reason i'm doing it is because I don't want to be prompted for entering the password, not even once.

I read about the "sudoers" way of doing what I need before posting the question here, but I didn't the like the idea of altering the sudoers file permanently(for personal and security reasons).

Although your solution does the job for me but I still don't get how this line works:

echo $PW | sudo -S [command]

From internet help:
sudo -S :  stdin, read the password from the standard input instead of the terminal.

echo : Display message on screen, writes each given STRING to standard output.

What's bugging me is that we are writing(echo) the output to standard output. Whereas we are reading(sudo -S) the input from standard input.

Does the standard input and the standard output mean the same here? Also what does this sentence mean : "from the standard input instead of the terminal"?

Thanks.

Regards

---

### Post by sisco311 on 2012-03-05
The pipe (`|') connects the standard output of a command to the standard input of another command. See: [http://mywiki.wooledge.org/BashGuide/InputAndOutput](http://mywiki.wooledge.org/BashGuide/InputAndOutput)

---

### Post by haseebifkaar on 2012-03-05
Thanks. I should have known this. My mistake.

Thanks All.

Regards

---

### Post by lechien73 on 2012-03-05
> **haseebifkaar said:**
> Thanks. I should have known this. My mistake.

Thanks All.

Regards

You're welcome :) if you're happy with the solution, could you please use the **Thread Tools** menu above the first post and mark the issue as [SOLVED]?

Thanks

---

### Post by Khayyam on 2012-03-05
> **haseebifkaar said:**
> [...]I read about the "sudoers" way of doing what I need before posting the question here, but I didn't the like the idea of altering the sudoers file permanently (for personal and security reasons).

In which case you fail to understand how sudoers works, a PAM based authentication will infact be more 'secure' than the use of a password held in plain text.

Also, the seperation of privileges (access control lists) exist for a reason, they are not simply an inconvienice created to bug the user with crys of "password". If your unfamilair with stdin/stdout/stderr, pipe, and the like, then the use of root privileges should approached with caution, and being prompted for a passphrase indicates that need for caution.

I can't remember how many times I've has this discussion, so many that I'm probably jaded. ACL's were designed to solve a problem, how to provide a means of operating multi-user systems, but this idea of shared resources has been replaced with the idea of "my computer" (although mostly these are still using shared resources via networking), so the expectation is 'my computer' = 'my privileges', but, back to the initial problem, this only works within the context of 'my resources' (which are actually mostly shared resources), and so much banging of heads ensue. The solution is mostly trivial, maintain ACL's and provide a means by which (specific) users can skirt them, but the notion of 'my computer' is the predominant paradigm and so gets to play the trump card "why ask me for a passphrase on my computer! Pax Tyrannous!". There is no arguing.

best ... khay

---

