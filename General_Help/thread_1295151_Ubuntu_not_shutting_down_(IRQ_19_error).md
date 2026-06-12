---
title: "Ubuntu not shutting down (IRQ 19 error)"
date: 2009-10-19
forum: General Help
---

### Post by barcelonic on 2009-10-19
Last night I tried adding a new repository to Synaptic Package Manager but typed it in wrong and couldnt open Synaptic Package Manager. After that I tried shutting down and it closed Ubuntu but then displayed a load of jibberish I couldnt understand. One of the lines however, said this: *"IRQ 19; nobody cared (try booting irqpoll)"*

Today I edited sources.list and removed the invalid line for the repository and now I have no problem running package manager, but that problem persists when I shut down.

My first questions is HOW do I shut down safely when that jibberish is displayed - so far I've been holding down the off button on my laptop but is that safe to do now after Ubuntu has closed or is there a safer way I should be doing it?

Secondly, is this problem harmful to my system and can I expect my Ubuntu 9.04 to stop booting altogether if I do not rectify this problem?

Thirdly, how do I fix it?? Id prefer not to reinstall Ubuntu because it's taken me ages to get all my software set up and configured. 

You should know I am a Linux noob. Any advice for me at all?

---

### Post by barcelonic on 2009-10-19
this problem has just seemed to disappear! could be bad but im going to assume its gone for good with no conflicting problems.

---

### Post by P4man on 2009-10-19
> **barcelonic said:**
> Last night I tried adding a new repository to Synaptic Package Manager but typed it in wrong and couldnt open Synaptic Package Manager. After that I tried shutting down and it closed Ubuntu but then displayed a load of jibberish I couldnt understand. One of the lines however, said this: *"IRQ 19; **nobody cared** (try booting irqpoll)"*

LMAO. Cant accuse the kernel developpers from lacking a sense of humor. ROFL.

Anyway, they are not only joking, they are also providing what could well be the solution: adding **irqpoll** to you kernel boot options. From some webpage, what it does:

> irqpoll         [HW]
                        When an interrupt is not handled search all handlers
                        for it. Also check all handlers each timer
                        interrupt. Intended to get systems with badly broken
                        firmware running.

If youre not sure how to add kernel parameters, have a look here:
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

replace the **VGA=775 **in that example with  ```
irqpoll
```

Alternatively, you could try check if there is an update for your bios that fixes the problem.

> Today I edited sources.list and removed the invalid line for the repository and now I have no problem running package manager, but that problem persists when I shut down.

Those problems are totally unrelated.

> My first questions is HOW do I shut down safely when that jibberish is displayed - so far I've been holding down the off button on my laptop but is that safe to do now after Ubuntu has closed or is there a safer way I should be doing it?

it depends what the jibberish says. It could be safe, but to answer the question: **R**aising **E**lephants **I**s **S**o **Ut**terly **B**oring. Or if you prefer, Reboot Even If System Utterly Broken

Remember one of them. Now hold down altgr + sysrq (usually same key as printscreen) then slowly type REISUB, always keeping down altgr and sysrq. That will safely reboot the machine (to power it off instead, replace the B at the end with O. And think of another mnemonic :) )

> 
Secondly, is this problem harmful to my system and can I expect my Ubuntu 9.04 to stop booting altogether if I do not rectify this problem?

If the filesystem is not synched, then yes its dangerous to shut down the machine inproperly. But there is a good chance the shutdown command went far enough that it was safe.
> 
Thirdly, how do I fix it?? Id prefer not to reinstall Ubuntu because it's taken me ages to get all my software set up and configured. 
see above and below :)

---

