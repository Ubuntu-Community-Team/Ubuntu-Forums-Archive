---
title: "PC Profile for Ubuntu 11.10"
date: 2012-04-03
forum: General Help
---

### Post by NRV on 2012-04-03
good day. am looking for a  PC profile information program that will display, in detail, the following information:

- OS
- System (PC) Model
- Processor
- Motherboard
- Memory
- Storage devices (hdd, dvd drive, etc..)
- other peripherals connected

OCS Inventory NG does this but it requires a server(?) i'm looking for a stand alone program (i can install on one pc) like belarc advisor. tia :)

---

### Post by Cheesemill on 2012-04-03
```
lshw -html > ~/report.html
```
Then open the report.html file that has been created in your home folder with your browser of choice.

---

### Post by NRV on 2012-04-06
thanks. will try this after the weekend.

---

