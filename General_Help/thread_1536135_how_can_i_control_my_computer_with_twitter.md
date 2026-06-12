---
title: "how can i control my computer with twitter"
date: 2010-07-21
forum: General Help
---

### Post by originalsurfmex on 2010-07-21
i was looking at tweetmypc - it looks so awesome to use my phone w/ twitter as a remote and send commands to my computer.  then i found twitaction, but the problem with it is that it can only update every minute and i want something that is checking all the time.

are there any other alternatives?

---

### Post by NFblaze on 2010-07-21
I do not think there is a program for that. Im sure you could make a script for it. Im not too sure on how to do this myself as I dont use Twitter nor am I superb at shell programming. Though it would probably involve using the commandline program Twurl and Awk.

Also, if your phone supports it you can use SSH to send commands straight to your computer.

Java- MidpSSH
Android- ConnectBot

---

### Post by originalsurfmex on 2010-07-21
this program does that:

[http://www.rakudave.ch/twitaction](http://www.rakudave.ch/twitaction)

but it limits me to checking every 1 minute, i would like ongoing checking of tweets.  it works like a charm, i'm planning on making bash scripts for special commands/sets of commands.

---

### Post by NFblaze on 2010-07-21
Well, he provided the source cod . Unfortunately, Ive never been good with programming and when I wanted to be I only look at Java 1 or 2. Though it looks like in the source code this 

```
	public void run() {
		while(true) {
			try {
				**Thread.sleep(60000*Integer.parseInt(interval.getModel().getValue().toString()));**
			} catch (NumberFormatException e) {
				System.out.println("Failed to read interval!");
			} catch (InterruptedException e) {}
			check.setEnabled(false);
			try {

```

Is the main code that controls how long the program waits before it iterates. You can either email the creator and ask him specifically what you need to change in order to make it faster. Or play with it yourself. Or ask someone who's more familiar with Java. Though everyone one minute is semi reasonable

Also, on a sidenote it looks like the program hasnt been updated since 2009. Twitter will be switching it's authentication method in like the upcoming months so this program may fail to work in the future. Might as well learn how to use Curl or Twurl and write your own script.

---

