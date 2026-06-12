---
title: "HP LaserJet 3030 print jobs are partially printed"
date: 2009-08-06
forum: General Help
---

### Post by mustbealennox on 2009-08-06
I am running Hardy Heron with the 2.6.24-24-generic kernel. I have an HP LaserJet 3030 connected to my computer with a printer cable.

First, the good news: I can scan with XSane and also print.

The bad news: most print jobs do not complete. A partial page may be printed, and then the print job stays in the queue with a  status of "processing". I can cancel the job and print again, and the same thing occurs - only a portion of the print job is printed and the rest gets stuck (for lack of a better technical term).

How can I go about debugging this further?

---

### Post by dcstar on 2009-08-07
> **mustbealennox said:**
> I am running Hardy Heron with the 2.6.24-24-generic kernel. I have an HP LaserJet 3030 connected to my computer with a printer cable.

First, the good news: I can scan with XSane and also print.

The bad news: most print jobs do not complete. A partial page may be printed, and then the print job stays in the queue with a  status of "processing". I can cancel the job and print again, and the same thing occurs - only a portion of the print job is printed and the rest gets stuck (for lack of a better technical term).

How can I go about debugging this further?

What sort of cable, USB or parallel?

---

### Post by mustbealennox on 2009-08-07
> What sort of cable, USB or parallel?

A parallel cable.

---

### Post by dcstar on 2009-08-07
> **mustbealennox said:**
> A parallel cable.

Check your BIOS settings for the port (experiment with the choices), and try another cable as the handshaking may not be working correctly.

---

### Post by hybenz on 2012-02-04
> **mustbealennox said:**
> I am running Hardy Heron with the 2.6.24-24-generic kernel. I have an HP LaserJet 3030 connected to my computer with a printer cable.

First, the good news: I can scan with XSane and also print.

The bad news: most print jobs do not complete. A partial page may be printed, and then the print job stays in the queue with a  status of "processing". I can cancel the job and print again, and the same thing occurs - only a portion of the print job is printed and the rest gets stuck (for lack of a better technical term).

How can I go about debugging this further?
Hi mustbealennox.. hope you could still read this.. but i am experiencing the same problem with my Hp laserjet 3030. how did you debugged the problem?

---

### Post by coffeecat on 2012-02-04
> **hybenz said:**
> Hi mustbealennox.. hope you could still read this..

Unlikely. The OP has not logged in for well over two years.

@hybenz, I see you have posted to another more recent thread. I suggest you add details of your printer to that one if you want help. It is far better to start your own thread if you need help.

This old thread closed.

---

