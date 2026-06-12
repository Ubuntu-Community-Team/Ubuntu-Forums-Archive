---
title: "bash question (I think)"
date: 2011-11-25
forum: General Help
---

### Post by g8vkv on 2011-11-25
Hello,

This is driving me bonkers.

I'm running mjpg_streamer and invoking it with the command ...

mjpg_streamer -i "input_uvc.so --resolution 800x600" -o "output_http.so -w var/www" -o "output_file.so -f /var/www/pics -d 300000"&

and it runs fine.

It generates the following output (which I've shortened)

 MJPG Streamer Version.: 2.0
 i: Using V4L2 device.: /dev/video0
   .. and then some other stuff, ending with ...
 o: command...........: disabled

to get the command prompt back, I then need to hit the return key.

Is there any way to get prompt back without having to hit the return? I thought running as a background process was supposed to return you to the prompt?

The reason I need to do this is that I have to run the command from within a script file and the script file isn't terminating.

I'm sure the answer is really simple, but it eludes me and it's driving me crazy.

Any help, pointers or advice would be appreciated.

Thanks in advance
g8vkv

---

### Post by gordintoronto on 2011-11-25
Put a space before the ampersand.

---

### Post by g8vkv on 2011-11-25
Hi,

Thanks for responding.

Yeah - did that already - no effect.

Also tried redirecting o/p and all kinds of things - no effect.

Finally found a solution using nohup - that resolves it.

I still can't understand why using & doesn't bring me back to the command prompt without having to hit return.

Might think about that later because it seems like odd behaviour.

Cheers
g8vkv

---

### Post by lsmithso on 2011-11-26
You're running a command in the background. Both the command and the shell are writing to the terminal at the same time, so one overwrites the other. The bash prompt is there, but its lost in the output of your command. This is the expected behaviour. 

nohup redirects the command output to nohup.out, thus you see the prompts as expected.

---

