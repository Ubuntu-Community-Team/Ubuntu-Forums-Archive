---
title: "How to know PC Health data?"
date: 2010-02-25
forum: General Help
---

### Post by saidbakr on 2010-02-25
Hello,

I need to know any application or applet that I can place it to the top panel which is able to display some data about Processor temperature, fan speed, etc.

I have done it in a previous installation of my Ubuntu 9.04 but I don't able to remember it. Any Ideas please?!

---

### Post by dcstar on 2010-02-25
> **saidbakr said:**
> Hello,

I need to know any application or applet that I can place it to the top panel which is able to display some data about Processor temperature, fan speed, etc.

I have done it in a previous installation of my Ubuntu 9.04 but I don't able to remember it. Any Ideas please?!

Install and configure the **lmsensors** package, then something like **gkrellm** or another tool to display things.

---

### Post by stinkeye on 2010-02-25
sensors-applet
hardware-monitor

both in synaptic

You may have to install lm-sensors and hddtemp as well.

---

