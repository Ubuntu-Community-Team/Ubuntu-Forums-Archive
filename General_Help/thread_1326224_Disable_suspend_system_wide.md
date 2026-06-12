---
title: "Disable suspend system wide"
date: 2009-11-14
forum: General Help
---

### Post by zardoz on 2009-11-14
Hello.

I am using an older laptop as a little server. The problem I have is that when closing the lid of the laptop while the login screen is presented (before logging in and before an user customized power management is activated) then the laptop goes into suspend mode. How do I change that system wide? What configuration file do I have to edit?

Best regards,
Kai

---

### Post by zardoz on 2009-11-14
Just found a solution (see here [http://jeremy.visser.name/2007/02/08/how-to-disable-suspend-and-hibernate-for-all-users-in-ubuntu/]("http://jeremy.visser.name/2007/02/08/how-to-disable-suspend-and-hibernate-for-all-users-in-ubuntu/"))

A copy & paste of the helping part (if the above link is unreachable):

```

How to disable Suspend and Hibernate for all users in Ubuntu
8 February 2007

I’ve known about this trick for a while now; just forgotten to blog about it.

Do you have a computer on which Suspend or Hibernate crashes, or is unstable? Is your computer shared? Do they tend to just click on everything they possibly can, then click Suspend, then OOPS! Look forward to a 5-minute fsck on next bootup! ;)

Well, here, I’m going to tell you how to remove the Suspend and/or Hibernate buttons in the Quit dialog in Ubuntu versions 6.06 and 6.10.

Step One

Press Alt+F2. A dialog box will come up entitled ‘Run Application’. In the text entry field, type:

    gksu gconf-editor

…and click ‘Run’. You may be prompted with your password, in which case, enter your password.
Step Two

An application named ‘Configuration Editor’ will come up. This program is for editing fine-grained details about your desktop. GNOME contains a database for storing your preferences called ‘gconf’. Configuration Editor is an application which edits the gconf database. Windows users may be familiar with the registry, which is a similar database.

In the Configuration Editor, navigate through the tree (located on the left-hand pane in the window) to:

    / &#8594; apps &#8594; gnome-power-manager

Step Three

In the right-hand pane, a new set of ‘keys’ have appeared. These keys are specific to the gnome-power-manager, which you selected in the previous step. Find the keys named ‘can_hibernate’ and ‘can_suspend’. Uncheck them both.

In Ubuntu version 6.06, the ‘can_suspend’ key is already unchecked. This is normal.
Step Four

Now, right-click on ‘can_hibernate’. From the context menu, choose Set as Mandatory. No dialog box will come up confirming that it worked, but I promise, it worked!

Do the same for ‘can_suspend’. Now, close the Configuration Editor.
Step Five

Log out of your system (From the System menu, choose Quit, then choose Log Out). Now log back in. You should now see that when you go to the Quit menu, the Suspend and Hibernate buttons are gone.

```

---

