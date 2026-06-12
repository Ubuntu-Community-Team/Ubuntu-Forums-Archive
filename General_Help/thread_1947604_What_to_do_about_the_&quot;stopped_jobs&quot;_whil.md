---
title: "What to do about the &quot;stopped jobs&quot; while closing a terminal?"
date: 2012-03-26
forum: General Help
---

### Post by arroy_0209 on 2012-03-26
When my work is completed, I generally press ctrl+D to close my terminal. Sometimes I get a comment that "there are stopped jobs" and the terminal is not closed. If I press ctrl+D again, the same comment may appear or sometimes the terminal is closed. Why does this happen? Does this mean that I made a mistake in closing some application? How to rectify that at this stage?

Second, is it safe to use kill -9 command to the PID of running application got from ps -aux command?

---

### Post by papibe on 2012-03-27
Hi arroy_0209.

Take a look at post.#4 of this [thread]("http://ubuntuforums.org/showthread.php?t=1947517").

You can list the stopped jobs by doing:
```
jobs -l
```
a typical output would be:
```
[1]-  5408 Stopped                 program1
[2]+  5409 Stopped (signal)        program2

```
If you exit the terminal those jobs will be killed. Before exiting you can send a job to the background so it keeps running if you run:
```
bg 1
```
where '1' is the job number, or send it to the foreground (as if you were running on the terminal) like this:
```
fg 1
```
Alternatively, you can kill a job by acceding it using the syntax %jobnumber. For instance:
```
kill %1
```

Hope that helps.
Regards.

---

### Post by arroy_0209 on 2012-03-27
Thanks for reply.

However I am not sure if this way of killing a job by issuing a command (kill %jobno.) is harmful or not. Now a days I am using a newly installed mathematics program where even after exiting it, I am getting the "there are stopped jobs" warning at the time of exiting terminal. I am a bit suspicious; exiting a program suitably should completely stop all the related processes. Now if some of these remain alive even after exiting and I "kill" those processes, will it not be harmful for the computer in the long run?

If we simply switch off the UPS, the computer will obviously stop but that is not the way we do. We "shut down" the machine and the machine stops after all the running processes are sequentially stopped. Switching off the machine will severely affect the machine in the long run. May be I am messing up things but can anybody please clarify?

---

### Post by evilsoup on 2012-03-27
I'm pretty sure that 'kill' just sends a signal to the program to close, it doesn't force it shut immediately but rather allows it to shut down gracefully.

'kill -9', however, *does* shut down a program instantly; and should only be used on misbehaving programs (that refuse to close with a regular 'kill' command).

---

### Post by SeijiSensei on 2012-03-27
"kill -15" tells a program to shut down "gracefully."  It's the preferred choice to stop a job.  If that doesn't work, you can resort to -9 and terminate it "with extreme prejudice."

Still I'd suggest you look into why you have those stopped jobs.  Perhaps they are child processes spawned by your math program.  Do they only happen when you use this program?  What happens if you type "fg" at the prompt after the "there are stopped jobs" error?

---

