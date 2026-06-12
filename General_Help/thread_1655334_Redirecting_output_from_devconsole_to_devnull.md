---
title: "Redirecting output from /dev/console to /dev/null"
date: 2010-12-29
forum: General Help
---

### Post by awp2513_ on 2010-12-29
Hi,

I'm using Ubuntu 10.4 Netbook Remix. When I reboot, there are several textual messages that appear before Plymouth is started and the splash screen is shown. I would like to "smooth" the look of the shutdown/reboot process (boot works just fine).

My goal is to hide this text, either by starting Plymouth sooner in the reboot/shutdown process or by changing the text that appears. I believe investigating the latter will prove more fruitful.

There are a variety of ways I could see to modify the text:

1.) Disable the logging (or whatever generates the text)
2.) Chaning the color to match the background (the text is "there" but not visible)
2.) Redirecting the output to something other than /dev/console (which is where I believe it is going to.

Most suggestions I've found have been to modify /etc/syslog.conf, which doesn't exist on my system. I've not been able to find a file analogous to it.

Things I've tried include the following:

1.) Editing /etc/10-console-messsages.conf:

```
kernel.printk = 1 1 1 7
```But this had no effect.

2.) Changing

```
console output|owner
```to

```
console none
```in several upstart scripts.

3.) A variety of attempts to change the colors of /dev/console

4.) before shutting down or rebooting:

```
rm /dev/console
ln /dev/null /dev/console
```This worked in that everything but the "The system is shutting down" message was not displayed, but /dev/console is restored when the system boots. Plus, this seems dirty (I'm sure I could be unwittingly pulling the rug out from under some process/service that expects /dev/console before I have a chance to restore the link.

Does anybody have suggestions for ways to modify the system such that this text is not displayed? 

Thanks!

---

