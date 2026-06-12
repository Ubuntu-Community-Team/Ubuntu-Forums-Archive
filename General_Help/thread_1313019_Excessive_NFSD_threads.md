---
title: "Excessive NFSD threads?"
date: 2009-11-03
forum: General Help
---

### Post by StrangeWill on 2009-11-03
```

root      2546     2  0 Oct21 ?        00:00:00 [nfsd4]                                                                                        
root      2547     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2548     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2549     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2550     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2551     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2552     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2553     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2554     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2555     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2556     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2557     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2558     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2559     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2560     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2561     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2562     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2563     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2564     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2565     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2566     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2567     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2568     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2569     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2570     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2571     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2572     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2573     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2574     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2575     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2576     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2577     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2578     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2579     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2580     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2581     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2582     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2583     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2584     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2585     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2586     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2587     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2588     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2589     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2590     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2591     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2592     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2593     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2594     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2595     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2596     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2597     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2598     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2599     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2600     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2601     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2602     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2603     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2604     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2605     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2606     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2607     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2608     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2609     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2610     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2611     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2612     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2613     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2614     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2615     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2616     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2617     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2618     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2619     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2620     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2621     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2622     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2623     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2624     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2625     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2626     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2627     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2628     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2629     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2630     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2631     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2632     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2633     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2634     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2635     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2636     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2637     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2638     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2639     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2640     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2641     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2642     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2643     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2644     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2645     2  0 Oct21 ?        00:00:00 [nfsd]                                                                                         
root      2646     2  0 Oct21 ?        00:00:00 [nfsd]  

```
I would file this under a bit excessive... would you not?

Why is it doing this? I run DRBL, but isn't NFSD suppose to load threads on demand, not like a million sleeping threads?

---

### Post by karlson on 2009-11-03
> **StrangeWill said:**
> I run DRBL, but isn't NFSD suppose to load threads on demand, not like a million sleeping threads?

Depends on your configuration.

NFSD always keeps a certain number of threads running.  Check /etc/default/nfs-kernel-server for the number as well as nfs-kernel-server 

Plus check what's connecting.

---

### Post by StrangeWill on 2009-11-04
> **karlson said:**
> Depends on your configuration.

NFSD always keeps a certain number of threads running.  Check /etc/default/nfs-kernel-server for the number as well as nfs-kernel-server 

Plus check what's connecting.

Well unless Samba uses it (err, dumb guess?), the only thing should be DRBL (I use it for ghosting), I do have it configured to allow [i]a lot[/i of machines, but typically only ghost one at a time. I'm guessing DRBL configured it to fire up all of the instances as soon as the server goes live, but again, I thought NFS would dynamically load threads, so I can just kick it down to 1 and the system will load of 40 if it needs them, correct?

---

