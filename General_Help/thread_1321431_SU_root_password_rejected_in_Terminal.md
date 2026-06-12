---
title: "SU root password rejected in Terminal"
date: 2009-11-10
forum: General Help
---

### Post by Yahoé on 2009-11-10
Since installing three PCs with 9.10, after changing the root password, the new password is rejected by the su command.

Please assist

---

### Post by MelDJ on 2009-11-10
did you do sudo su?

---

### Post by Yahoé on 2009-11-10
Thanks for your answer. sudo su? Why would I do that. su is a command on its own. What are you getting at my friend?

---

### Post by P4man on 2009-11-10
> **Yahoé said:**
> Since installing three PCs with 9.10, after changing the root password, the new password is rejected by the su command.


Why did you change the root password?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Yahoé on 2009-11-10
Thanks for the links.
When installing a system I like to have the root account password, it can come in easy when using te recovery console for example.
I had been using the alpha version of 9.10 for a while now and had been using the root account from Terminal without having to enable it, just after changing the password using the GUI.
On 9.10 final I can enable the account with "sudo passwd root" and giving it the password I want. When, after, trying to change the password again using the GUI, the new password is rejected in terminal by the "su" command, the one set with "sudo passwd root"[FONT=monospace]. I'm not sure I understand why,and why the final version reacts diffrently than the pre-final ones. Unless I'm missing something all together...
[/FONT]

---

### Post by coffeecat on 2009-11-10
> **Yahoé said:**
> What are you getting at my friend?

Your friend is referring to the Ubuntu security model. You might want to take time to read and think about it rather than make assumptions about how you escalate to root privileges. P4man has already provided the link, but I'll do so again.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Yahoé on 2009-11-10
As I had answered to P4Man, thanks for the links guys. It's doesn't answer all my questions, but that'll do just fine.

Regards

---

### Post by anaconda on 2009-11-10
> **Yahoé said:**
> Thanks for the links.
When installing a system I like to have the root account password, it can come in easy when using te recovery console for example.
I had been using the alpha version of 9.10 for a while now and had been using the root account from Terminal without having to enable it, just after changing the password using the GUI.
On 9.10 final I can enable the account with "sudo passwd root" and giving it the password I want. When, after, trying to change the password again using the GUI, the new password is rejected in terminal by the "su" command, the one set with "sudo passwd root"[FONT=monospace]. I'm not sure I understand why,and why the final version reacts diffrently than the pre-final ones. Unless I'm missing something all together...
[/FONT]

sounds strange.
su should accept the root password, if it exist. 

Does the root password work in other situations?
eg. in recovery mode?
Did you reboot after giving root a password(shouldn't be necessary, but who knows.)

PS. I don't like the forum policy of NOT assisting with Root problems. There ARE valid reasons to enable the root account. But maybe not for "normal" users...

---

### Post by P4man on 2009-11-10
> **anaconda said:**
> sounds strange.
PS. I don't like the forum policy of NOT assisting with Root problems. There ARE valid reasons to enable the root account. 

Perhaps. But "liking to have a root account" or  "easy when using te recovery console for example" do not qualify as good reasons IMHO. Having bricked his system now I guess proves that point.

---

### Post by sisco311 on 2009-11-10
> **anaconda said:**
> 
PS. I don't like the forum policy of **NOT assisting with Root problems.** There ARE valid reasons to enable the root account. But maybe not for "normal" users...

Where did you read that?

The forum policy is clear:
> 
Tutorials explaining **how to enable the root account for a graphical login or autologin** will not be supported on the forums and will be moved to the Jail. Although we believe people should have the freedom to run their computers however they want, we also believe in supporting Ubuntu's security model. You can find or post information elsewhere on the internet regarding **graphical Ubuntu root logins**; such tutorials do not have to be hosted on the Ubuntu Forums.

[thread=716201]Forum policy on log-in-as-root tutorials[/thread]

---

### Post by coffeecat on 2009-11-10
> **anaconda said:**
> There ARE valid reasons to enable the root account.

Maybe, maybe not, but if people burble about it all over this forum, they'll confuse newcomers to Ubuntu who are well served by the Ubuntu security model. In fact Linux experts are well served by the Ubuntu security model. It's only self-appointed experts who, perhaps, are not so expert, that feel limited by it, and who feel the need to tinker (and bork).

IMHO. :wink:

> **P4man said:**
> Perhaps. But "liking to have a root account" or  "easy when using te recovery console for example" do not qualify as good reasons IMHO. Having bricked his system now I guess proves that point.

:) Agreed.

---

