---
title: "eth0: hw csum failure"
date: 2010-04-01
forum: General Help
---

### Post by msp3k on 2010-04-01
I have several machines that lose their network randomly with the following error:

```

kernel: [165968.835696] sky2 eth0: rx length error: status 0x5cc0100 length 2364
kernel: [165969.767987] eth0: hw csum failure.
kernel: [165969.768001] Pid: 0, comm: swapper Tainted: P           2.6.31-20-generic #58-Ubuntu
kernel: [165969.768007] Call Trace:
kernel: [165969.768012]  <IRQ>  [<ffffffff81439f5d>] netdev_rx_csum_fault+0x3d/0x40
kernel: [165969.768037]  [<ffffffff8143497b>] __skb_checksum_complete_head+0x5b/0x70
kernel: [165969.768046]  [<ffffffff8143499c>] __skb_checksum_complete+0xc/0x10
kernel: [165969.768056]  [<ffffffff814a9498>] nf_ip_checksum+0x58/0x120
kernel: [165969.768081]  [<ffffffffa08afac3>] tcp_error+0xa3/0x230 [nf_conntrack]
kernel: [165969.768092]  [<ffffffff81053768>] ? try_to_wake_up+0x118/0x340
kernel: [165969.768111]  [<ffffffffa08abedf>] nf_conntrack_in+0x11f/0x4d0 [nf_conntrack]
kernel: [165969.768119]  [<ffffffff8105399d>] ? default_wake_function+0xd/0x10
kernel: [165969.768129]  [<ffffffff81130561>] ? pollwake+0x51/0x60
kernel: [165969.768138]  [<ffffffff81111266>] ? get_partial_node+0x86/0xa0
kernel: [165969.768147]  [<ffffffff81045c49>] ? __wake_up_common+0x59/0x90
kernel: [165969.768159]  [<ffffffffa08c057c>] ipv4_conntrack_in+0x1c/0x20 [nf_conntrack_ipv4]
kernel: [165969.768169]  [<ffffffff8145f7c4>] nf_iterate+0x64/0xa0
kernel: [165969.768177]  [<ffffffff814671d0>] ? ip_rcv_finish+0x0/0x460
kernel: [165969.768185]  [<ffffffff8145f8a6>] nf_hook_slow+0xa6/0x100
kernel: [165969.768193]  [<ffffffff814671d0>] ? ip_rcv_finish+0x0/0x460
kernel: [165969.768201]  [<ffffffff81467d63>] ip_rcv+0x263/0x350
kernel: [165969.768210]  [<ffffffff8143d4aa>] netif_receive_skb+0x38a/0x5d0
kernel: [165969.768218]  [<ffffffff8143d898>] napi_skb_finish+0x48/0x60
kernel: [165969.768226]  [<ffffffff8143dd94>] napi_gro_receive+0x34/0x40
kernel: [165969.768261]  [<ffffffffa014148b>] sky2_status_intr+0x55b/0x610 [sky2]
kernel: [165969.768277]  [<ffffffffa014159d>] sky2_poll+0x5d/0xc0 [sky2]
kernel: [165969.768286]  [<ffffffff8143df47>] net_rx_action+0x107/0x250
kernel: [165969.768295]  [<ffffffff81082037>] ? getnstimeofday+0x57/0xe0
kernel: [165969.768305]  [<ffffffff8107c9c1>] ? ktime_get_ts+0x51/0x70
kernel: [165969.768314]  [<ffffffff810653dd>] __do_softirq+0xbd/0x200
kernel: [165969.768323]  [<ffffffff8101326c>] call_softirq+0x1c/0x30
kernel: [165969.768330]  [<ffffffff81014c45>] do_softirq+0x55/0x90
kernel: [165969.768338]  [<ffffffff81065145>] irq_exit+0x85/0x90
kernel: [165969.768345]  [<ffffffff81014180>] do_IRQ+0x70/0xe0
kernel: [165969.768354]  [<ffffffff81012a93>] ret_from_intr+0x0/0x11
kernel: [165969.768359]  <EOI>  [<ffffffff812dc3cd>] ? acpi_idle_enter_bm+0x28b/0x2bf
kernel: [165969.768375]  [<ffffffff812dc3c6>] ? acpi_idle_enter_bm+0x284/0x2bf
kernel: [165969.768385]  [<ffffffff814018bb>] ? cpuidle_idle_call+0x9b/0x100
kernel: [165969.768393]  [<ffffffff81010e52>] ? cpu_idle+0xb2/0x100
kernel: [165969.768402]  [<ffffffff81518356>] ? rest_init+0x66/0x70
kernel: [165969.768413]  [<ffffffff8183e039>] ? start_kernel+0x352/0x35b
kernel: [165969.768422]  [<ffffffff8183d59a>] ? x86_64_start_reservations+0x125/0x129
kernel: [165969.768432]  [<ffffffff8183d698>] ? x86_64_start_kernel+0xfa/0x109

```

Since the user's home area is automounted this immediately causes the interface to lock up, and of course it's not possible to SSH in remotely.  If I can get to the console then I can usually do a ctrl+alt+F1 to get to a terminal login and get in as root.  Then, using "ifdown eth0 ; ifup eth0" will make the error messages about csum failures go away, but NFS never seems to recover, so the only real fix that I can see is to reboot the machine.

Most posts I've found on the network involve people talking about a VirtualBox bug from 2008 that's supposedly fixed by now.  We have virtualbox installed (and therefore have the modules loaded), but this problem only seems to happen on a small number of hosts, and it happens for people who don't run virtualbox.

What does this mean, and is there a fix?

Running Ubuntu Karmic (9.10) amd64
Kernel: 2.6.31-20-generic
lspci: Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)

Any help appreciated,

Michael

---

