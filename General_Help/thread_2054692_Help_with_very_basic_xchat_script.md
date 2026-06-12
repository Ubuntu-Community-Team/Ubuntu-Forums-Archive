---
title: "Help with very basic xchat script"
date: 2012-09-07
forum: General Help
---

### Post by homemadejam on 2012-09-07
Hey guys.

(Sorry if I have posted this in the wrong forum...)

So the Minecraft server I'm a mod on has just linked up it's chat with an IRC. Whem I'm on the IRC, it's normally spammed out by "username has hit the ground too hard", or other death messages.

I've been trying to write a simple plugin that will stop these messages from appearing. This is what I have so far:

```

Xchat::register( "Hide Deaths", "0.1" );
Xchat::hook_print( "hit the ground too hard", sub { return Xchat::EAT_XCHAT });
Xchat::hook_print( "was slain by", sub { return Xchat::EAT_XCHAT });
Xchat::hook_print( "tried to swim in lava", sub { return Xchat::EAT_XCHAT });
Xchat::hook_print( "fell out of the world", sub { return Xchat::EAT_XCHAT });
Xchat::hook_print( "was pricked to death", sub { return Xchat::EAT_XCHAT });
Xchat::hook_print( "burned to death", sub { return Xchat::EAT_XCHAT });
Xchat::hook_print( "was shot by", sub { return Xchat::EAT_XCHAT });

```

I save as no_deaths.pl in my ~/.xchat2 directory so it is automaticaly loaded.

However, I'm still seeing all of these types of messages. Any idea what I'm doing wrong?

Thanks in advance.

---

### Post by kostkon on 2012-09-07
It doesn't work like this, you have to provide hook_print the xchat event and not the message itself. Please, read again the [xchat perl interface doc]("http://xchat.org/docs/xchat2-perl.html").

For example, in your case you want to intercept all the channels messages, so:
```
Xchat::hook_print( "Channel Message", sub ... );
```
etc... haven't programmed in Perl.

Your callback should do the checking and return Xchat::EAT_ALL when it finds a match and Xchat::EAT_NONE when it doesn't.

Hope that helps.

---

### Post by homemadejam on 2012-09-08
Thanks for pushing me in the right direction!
I'll check out that link you provided.

---

