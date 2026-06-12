---
title: "zeitgeist-datah zombie"
date: 2012-04-13
forum: General Help
---

### Post by ihatetryingtopickaloginna on 2012-04-13
What is a zombie in Linux?

---

### Post by uRock on 2012-04-13
Found this answer on [askubuntu.com]("http://askubuntu.com/questions/48624/what-are-zombie-processes"),> Zombies are DEAD processes. They can not be 'kill' (You cannot kill the DEAD). All processes eventually die, and when they do they become zombies. They consume almost no resources, which is to be expected because they are dead! The reason for zombies is so the zombie's parent (process) can retrieve the zombie's exit status and resource usage statistics. The parent signals the operating system that it no longer needs the zombie by using one of the wait() system calls.

When a process dies, its child processes all become children of process number 1, which is the init process. Init is ``always'' waiting for children to die, so that they don't remain as zombies.

If you have zombie processes it means those zombies have not been waited for by their parent (look at PPID displayed by ps -l). You have three choices: Fix the parent process (make it wait); kill the parent; or live with it. Remember that living with it is not so hard because zombies take up little more than one extra line in the output of ps.

Zombies can be identified in the output from the Unix ps command by the presence of a "Z" in the STAT column. Zombies that exist for more than a short period of time typically indicate a bug in the parent program. As with other leaks, the presence of a few zombies isn't worrisome in itself, but may indicate a problem that would grow serious under heavier loads.

To remove zombies from a system, the SIGCHLD signal can be sent to the parent manually, using the kill command. If the parent process still refuses to reap the zombie, the next step would be to remove the parent process. When a process loses its parent, init becomes its new parent. Init periodically executes the wait system call to reap any zombies with init as parent.

There are also orphan processes which are a computer process whose parent process has finished or terminated.

A process can become orphaned during remote invocation when the client process crashes after making a request of the server.

Orphans waste server resources and can potentially leave a server in trouble (This is the biggest resource difference between zombies and orphans (Except if you see some orphan zombie movie). However there are several solutions to the orphan process problem:

Extermination is the most commonly used technique; in this case the orphan process is killed.

Reincarnation is a technique in which machines periodically try to locate the parents of any remote computations; at which point orphaned processes are killed.

Expiration is a technique where each process is allotted a certain amount of time to finish before being killed. If need be a process may "ask" for more time to finish before the allotted time expires.

A process can also be orphaned running on the same machine as its parent process. In a UNIX-like operating system any orphaned process will be immediately adopted by the special "init" system process. This operation is called re-parenting and occurs automatically. Even though technically the process has the "init" process as its parent, it is still called an orphan process since the process which originally created it no longer exists.

---

### Post by ihatetryingtopickaloginna on 2012-04-14
Thanks for the reply.

---

