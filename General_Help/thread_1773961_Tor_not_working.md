---
title: "Tor not working"
date: 2011-06-02
forum: General Help
---

### Post by joelstitch on 2011-06-02
I installed Tor a few days ago and it was working perfectly. Today I tried using it and it would want to enter any .onion website even though the check.torproject.com website said that my computer was using Tor. So I decited to completely remove Tor, Vidalia, Privoxy and Polipo and do a reinstallation of Tor and all the components. I follow these instructions:

> 1 nano /etc/apt/sources.list
add:
[FONT=courier]BASH-Code:[/FONT]
1 deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) lucid main


[FONT=courier]BASH-Code:[/FONT]
1 2 $ sudo apt-get update $ sudo apt-get install tor vidalia privoxy


Setup Privoxy
[FONT=courier]BASH-Code:[/FONT]
1 nano /etc/privoxy/config


and add
[FONT=courier]BASH-Code:[/FONT]
1 forward-socks4a    /    [COLOR=#cc66cc]127.0[/COLOR][COLOR=#cc66cc].0[/COLOR][COLOR=#cc66cc].1[/COLOR]:[COLOR=#cc66cc]9050[/COLOR] .


[FONT=courier]BASH-Code:[/FONT]
1 /etc/init.d/privoxy restart

I have the Tor Button installed on Firefox. Now when I open Vidalia I get this error:

> Unexpected Error

Vidalia detected that the Tor software exited unexpectedly.And the Message Log says:

> Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Failed to parse/validate config: Failed to bind one of the listener ports.
Anybody have a solution?

---

### Post by joelstitch on 2011-06-02
Well nevermind, I found the solution here:

[http://www.noobrescue.com/blog/vidalia-detected-that-the-tor-software-exited-unexpectedly](http://www.noobrescue.com/blog/vidalia-detected-that-the-tor-software-exited-unexpectedly)

> **First step:** is to open the configuration file of tor. Open a terminal and input this command:
  sudo gedit /etc/tor/torrc
  After the file opens, scroll down to line 53 to line 60 and you will see something like this:
  ## The port on which Tor will listen for local connections from Tor ## controller applications, as documented in control-spec.txt. #ControlPort 9051 ## If you enable the controlport, be sure to enable one of these ## authentication methods, to prevent attackers from accessing it. #HashedControlPassword 16:872860B76453A77D60CA2BB8C1A7042072093276A3D701AD684053EC4C #CookieAuthentication 1 
  **Second Step:** Remove # from #ControlPort 9051 so line 55 looks like this:
 ControlPort 9051
  Then enable password authentication by removing # from #HashedControlPassword so line 58 looks like this:
 HashedControlPassword
  **Third Step:** Input the following command into the terminal to  create a password for tor, but where it says, “mypassword,” replace that  with a password of your choosing:
  tor --hash-password mypassword
  The terminal will respond with a hash that looks like this:
  16:816172DEB125A9CA603A6A8A5C16D0642DA4556E4EC417E6B9AAC9AF0D
  Copy this entire hash string, and then replace the defauld value on line 58.
  This is how our torrec file looked like when we finished configuring it:
  ## The port on which Tor will listen for local connections from Tor ## controller applications, as documented in control-spec.txt. ControlPort 9051 ## If you enable the controlport, be sure to enable one of these ## authentication methods, to prevent attackers from accessing it. #HashedControlPassword 16:816172DEB125A9CA603A6A8A5C16D0642DA4556E4EC417E6B9AAC9AF0D #CookieAuthentication 1 
  **Fourth Step:** Save the torrc file: *ctrl + s* and close it. Then restart tor by inputing this to a terminal:
  sudo /etc/init.d/tor restart
  That's it! Open Vidalia and it should now be able to start and stop tor without a problem.


---

