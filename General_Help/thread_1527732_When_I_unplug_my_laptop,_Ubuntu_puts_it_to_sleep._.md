---
title: "When I unplug my laptop, Ubuntu puts it to sleep. Why?"
date: 2010-07-09
forum: General Help
---

### Post by cookie6 on 2010-07-09
I just installed Ubuntu on my Acer Aspire One, and when I unplug my laptop, the screen goes dark, and it puts my laptop to sleep. Why does  it do that, and how can I fix it? Thanks.

---

### Post by steveneddy on 2010-07-09
Because it doesn't like you?

Seriously - go to 

System --> Preferences --> Power Management

Click on the "On Battery Power" tab at the top.

Are there any settings there that may help you? Maybe on the other tabs.

I don't see anything on my laptop for sleeping when pulling the power - but your may be different.

Her are some links to help you debug the power manager:

[https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager)

Hmmmm.

try opening gconfig editor 0 in terminal

```
gconf-editor
```

go to 

apps --> gnome-power-manager --> timeouts

at the top - where it says

"sleep_computer_ac" and change the value to 0 if it is a 1

or maybe the "sleep_computer_battery" is on - these should both be a zero value.

---

### Post by cookie6 on 2010-07-09
> **steveneddy said:**
> Because it doesn't like you?

Seriously - go to 

System --> Preferences --> Power Management

Click on the "On Battery Power" tab at the top.

Are there any settings there that may help you? Maybe on the other tabs.

I don't see anything on my laptop for sleeping when pulling the power - but your may be different.

Her are some links to help you debug the power manager:

[https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager)

Hmmmm.

try opening gconfig editor 0 in terminal

```
gconf-editor
```go to 

apps --> gnome-power-manager --> timeouts

at the top - where it says

"sleep_computer_ac" and change the value to 0 if it is a 1

or maybe the "sleep_computer_battery" is on - these should both be a zero value.

Yup, "sleep_computer_ac' is at 0, and "sleep_computer_battery" is on. They are both on 0.

---

### Post by Sonsum on 2010-07-09
> **cookie6 said:**
> Yup, "sleep_computer_ac' is at 0, and "sleep_computer_battery" is on. They are both on 0.

I think this is an Acer AspireOne hardware issue.

Try setting the option for "On Lid Close" in the power manager settings from standby to blank screen.

It apparently worked [here]("http://ubuntuforums.org/showthread.php?t=1278765")

---

### Post by scradock on 2010-07-09
This happens to me sometimes; it's a sign that my battery died, so when I unplug there isn't enough power to keep the machine running.

Is your problem the same? Check the battery state......

---

