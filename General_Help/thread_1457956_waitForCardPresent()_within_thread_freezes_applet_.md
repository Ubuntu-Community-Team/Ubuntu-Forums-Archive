---
title: "waitForCardPresent() within thread freezes applet under Ubuntu"
date: 2010-04-19
forum: General Help
---

### Post by bilss on 2010-04-19
Hello,

I am currently having some issues with the waitForCardPresent() function  in a Java applet.

I am developping an applet that manages PC/SC communications. 
In my applet I need to check card Status. 
To do I use a Thread , I have created a CardStatus class that manages  the work of the thread (this class extends Thread).

Here is how I start my thread : 
cs = new CardStatus();
cardStatusThread = new Thread(cs);
cardStatusThread.start();

I use EventListeners to notify my applet once waitForCardPresent()  has  finished.

The run() of my thread consists of (I have simplified the code) :
```

        while(true)
        {
            if(Reader != null)
            {
                
                try {
                    if(!Reader.isCardPresent()) // the reader is set by the applet  using a SetReader() function defined in CardStatus class
                                        {
                        Reader.waitForCardPresent(0); 
                                    this.NotifyPresentListeners(); // this  function notifies the applet that a card has been found
                                        }
                    
                } catch (CardException e) {
                    // TODO Auto-generated catch block
                    e.printStackTrace();
                }
            }
```This applet is signed.
I successfully manage to run this applet using windows, but I can't when  using Ubuntu : the applet freezes until I put a card in the reader.

I have tried to replace the Reader.waitForCardPresent(0); instruction  with Thread.sleep(50000); to check if there was a mistake from the way I  was using my thread,  in that case my applet doesn't freeze under  Ubuntu ; so I am guessing that it is the waitForCardPresent function  that causes the trouble.

I know that it could not be a security issue, because I have created an  un signed applet that uses WaitForCardPresent (not within a thread,  within the main code of the applet, just to test this) and I had no  problem with it.

---

### Post by bilss on 2010-04-22
I re arranged a bit my code and put more displays to get a better  idea of what's going on.

I now know what is causing this : the waitForCardPresent method throws  the following Exception :   javax.smartcardio.CardException: wait  mismatch
        at  sun.security.smartcardio.TerminalImpl.waitForCard(TerminalImpl.java:103)
	at  sun.security.smartcardio.TerminalImpl.waitForCardPresent(TerminalImpl.java:116)

I have searched a bit around for this exception and found this : 
[http://lxr.js-home.org/lxr/source/su...minalImpl.java]("http://lxr.js-home.org/lxr/source/sun/security/smartcardio/TerminalImpl.java")

Apparently this exception is thrown when a card isn't present and the  timeout as expired, but I set the timeout to 0 (TIMEOUT INFINITE).  Replacing 0 with TIMEOUT_INFINITE (0xffffffff) doesn't work.

Any idea why do get this exception?

---

