---
title: "No internet connection win7"
date: 2011-10-24
forum: General Help
---

### Post by SudoNOM on 2011-10-24
After installing wubi, I have to rely on my wifi for win7 connection? even though ubuntu is running on wired connection.

---

### Post by Paddy Landau on 2011-10-24
Installing WUBI should not affect your Windows installation in any way.

I'm no longer a Windows expert, but go to your Network Manager from your Windows Control Panel and see if you can diagnose the problem using Windows's built-in trouble-shooting function.

---

### Post by Mark Phelps on 2011-10-24
I had a similar problem with a dual-boot PC using a Realtek LAN chipset.  Whenever I rebooted from Ubuntu (10.10) back into Win7, the wired connection no longer worked.  Would have to reset it using a Realtek LAN Diagnostic routine -- which fortunately, was provided with the LAN drivers.

It took a couple of driver updates for the LAN chipset before this problem was solved.

So, as Paddy has said, you may have to mess around with running LAN diagnostics to see if the wired connection can be reset.  That is what I had to do -- reset the connection each time.

---

