---
title: "error while updating"
date: 2011-01-21
forum: General Help
---

### Post by hunterkasy on 2011-01-21
I am running ubuntu 10.04 lts of a dell inspiron 600m I went to the update manager and updated all available updates after it was done I got this error in the update manager window:

An error occurred
The following details are provided:

E: linux-image-2.6.32-26-generic: subprocess installed post-installation script returned error exit status 1

I don't know much about linux so I don't know if it is ok or if it needs to be fixed, or how to fix it any help will be appreciated

---

### Post by Rubi1200 on 2011-01-22
Hi,
try the following commands in the terminal;

```
sudo apt-get install -f

sudo dpkg --configure -a
```

Post back with errors, if any.

---

### Post by hunterkasy on 2011-01-25
> **Rubi1200 said:**
> Hi,
try the following commands in the terminal;

```
sudo apt-get install -f

sudo dpkg --configure -a
```

Post back with errors, if any.

I tried both commands in the terminal:

I did the sudo apt-get install -f and let it go through the process when that was done I did the second one sudo dpkg --configure -a and let that go through then I copied the terminal as a whole and pasted it here

t_pkttype.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_sane.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_CONNMARK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_iprange.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_ftp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_h323.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_HL.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_netlink.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_multiport.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_dh.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_rr.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_ftp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_nq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_wrr.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_wlc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_sh.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_comment.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_socket.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_SECMARK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_TRACE.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_proto_udplite.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_CONNSECMARK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_CLASSIFY.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_TCPMSS.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_NFQUEUE.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nfnetlink.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_state.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_LED.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_helper.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nfnetlink_log.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_hashlimit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nfnetlink_queue.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_tcpudp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_connmark.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_tftp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/x_tables.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_length.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_recent.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_hl.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_connbytes.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_RATEEST.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_NOTRACK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_irc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_osf.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_sctp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_proto_dccp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_string.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_connlimit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_NFLOG.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_physdev.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_cluster.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_owner.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_dccp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_u32.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_conntrack.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_rateest.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_statistic.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_quota.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_dscp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_proto_sctp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_realm.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_time.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_netbios_ns.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_mark.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_tcpmss.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netrom/netrom.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_police.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_basic.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_route.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_teql.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_simple.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_nbyte.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_prio.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_atm.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_u32.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_hfsc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_rsvp6.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_rsvp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_nat.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_tbf.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_fw.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_red.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_text.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_dsmark.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_htb.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_sfq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_gred.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_cbq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_gact.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_ingress.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_mirred.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_skbedit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_cmp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_meta.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_pedit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_flow.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_netem.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_u32.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_ipt.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_multiq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_drr.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_tcindex.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sctp/sctp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/phonet/pn_pep.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/phonet/phonet.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/sunrpc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/auth_gss/rpcsec_gss_spkm3.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/auth_gss/auth_rpcgss.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/auth_gss/rpcsec_gss_krb5.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rxrpc/rxkad.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rxrpc/af-rxrpc.ko: Exec format error
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_pptp.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_lc.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_lblc.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_sed.ko
Failed to run depmod
dpkg: error processing linux-image-2.6.32-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.32-26-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
brady@brady-laptop:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.32-26-generic (2.6.32-26.48) ...
Running depmod.
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rose/rose.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rds/rds_rdma.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rds/rds.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rds/rds_tcp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_proto_gre.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_sip.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_mac.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_esp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_limit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_MARK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_amanda.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_DSCP.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_policy.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_tproxy_core.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_TPROXY.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_pkttype.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_sane.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_CONNMARK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_iprange.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_ftp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_h323.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_HL.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_netlink.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_multiport.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_dh.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_rr.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_ftp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_nq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_wrr.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_wlc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_sh.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_comment.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_socket.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_SECMARK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_TRACE.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_proto_udplite.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_CONNSECMARK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_CLASSIFY.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_TCPMSS.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_NFQUEUE.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nfnetlink.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_state.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_LED.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_helper.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nfnetlink_log.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_hashlimit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nfnetlink_queue.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_tcpudp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_connmark.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_tftp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/x_tables.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_length.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_recent.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_hl.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_connbytes.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_RATEEST.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_NOTRACK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_irc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_osf.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_sctp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_proto_dccp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_string.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_connlimit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_NFLOG.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_physdev.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_cluster.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_owner.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_dccp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_u32.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_conntrack.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_rateest.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_statistic.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_quota.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_dscp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_proto_sctp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_realm.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_time.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_netbios_ns.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_mark.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_tcpmss.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netrom/netrom.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_police.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_basic.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_route.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_teql.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_simple.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_nbyte.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_prio.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_atm.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_u32.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_hfsc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_rsvp6.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_rsvp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_nat.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_tbf.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_fw.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_red.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_text.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_dsmark.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_htb.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_sfq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_gred.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_cbq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_gact.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_ingress.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_mirred.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_skbedit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_cmp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_meta.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_pedit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_flow.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_netem.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_u32.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_ipt.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_multiq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_drr.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_tcindex.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sctp/sctp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/phonet/pn_pep.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/phonet/phonet.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/sunrpc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/auth_gss/rpcsec_gss_spkm3.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/auth_gss/auth_rpcgss.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/auth_gss/rpcsec_gss_krb5.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rxrpc/rxkad.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rxrpc/af-rxrpc.ko: Exec format error
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_pptp.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_lc.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_lblc.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_sed.ko
Failed to run depmod
dpkg: error processing linux-image-2.6.32-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.32-26-generic
brady@brady-laptop:~$

---

### Post by hunterkasy on 2011-01-25
I am adding more info from sys info, maybe the extra info can help to find out a solution

I am sure it is more info about my system that you need, but I figure what the hell

System information report, generated by Sysinfo: 1/25/2011 4:50:34 PM
[http://sourceforge.net/projects/gsysinfo](http://sourceforge.net/projects/gsysinfo)

SYSTEM INFORMATION
	Running Ubuntu Linux, the Ubuntu 10.04 (lucid) release.
	GNOME: 2.30.2 (Ubuntu 2010-06-25)
	Kernel version: 2.6.32-27-generic (#49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010)
	GCC: 4.4.3 (i486-linux-gnu)
	Xorg: unknown (10 December 2010  05:53:04PM) (10 December 2010  05:53:04PM)
	Hostname: brady-laptop
	Uptime: 0 days 0 h 38 min

CPU INFORMATION
	GenuineIntel, Intel(R) Pentium(R) M processor 1.50GHz
	Number of CPUs: 1
	CPU clock currently at 1500.000 MHz with 2048 KB cache
	Numbering: family(6) model(13) stepping(6)
	Bogomips: 2997.54
	Flags: fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2

MEMORY INFORMATION
	Total memory: 497 MB
	Total swap: 1223 MB

STORAGE INFORMATION
	SCSI device -  scsi0
		Vendor:  ATA      
		Model:  IC25N030ATMR04-0 
	SCSI device -  scsi1
		Vendor:  TEAC     
		Model:  DVD-ROM DV-28E-C 

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		Intel Corporation 82855PM Processor to I/O Controller (rev 03)
	PCI bridge(s)
		Intel Corporation 82855PM Processor to AGP Controller (rev 03)
		Intel Corporation 82801 Mobile PCI Bridge (rev 81)
	USB controller(s)
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
		Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
	ISA bridge
		Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
	IDE interface
		Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
		Subsystem: Intel Corporation Device 4541

GRAPHIC CARD
	VGA controller
		ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
		Subsystem: Dell Device 011e

SOUND CARD
	Multimedia controller
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
		Subsystem: Dell Device 011e

NETWORK
	Network controller
		Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
		Subsystem: Intel Corporation Device 2565
	Ethernet controller
		Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
		Subsystem: Dell Device 865d
	Modem
		Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
		Subsystem: Conexant Systems, Inc. Device 5422

---

### Post by plucky on 2011-01-26
I think you have a corrupt downloaded .deb file.Try running ```
sudo apt-get clean
``` which will delete all the previous downloaded files from the /var/cache/apt/archives location.

Then run the ```
sudo apt-get install -f
``` which will the download a new set of .deb files and see if that makes a difference.

Good Luck

---

### Post by hunterkasy on 2011-01-26
I tried both commands and this is what I get:

brady@brady-laptop:~$ sudo apt-get clean
brady@brady-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-26-generic (2.6.32-26.48) ...
Running depmod.
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rose/rose.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rds/rds_rdma.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rds/rds.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rds/rds_tcp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_proto_gre.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_sip.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_mac.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_esp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_limit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_MARK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_amanda.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_DSCP.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_policy.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_tproxy_core.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_TPROXY.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_pkttype.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_sane.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_CONNMARK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_iprange.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_ftp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_h323.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_HL.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_netlink.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_multiport.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_dh.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_rr.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_ftp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_nq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_wrr.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_wlc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_sh.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_comment.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_socket.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_SECMARK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_TRACE.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_proto_udplite.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_CONNSECMARK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_CLASSIFY.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_TCPMSS.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_NFQUEUE.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nfnetlink.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_state.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_LED.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_helper.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nfnetlink_log.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_hashlimit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nfnetlink_queue.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_tcpudp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_connmark.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_tftp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/x_tables.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_length.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_recent.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_hl.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_connbytes.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_RATEEST.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_NOTRACK.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_irc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_osf.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_sctp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_proto_dccp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_string.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_connlimit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_NFLOG.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_physdev.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_cluster.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_owner.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_dccp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_u32.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_conntrack.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_rateest.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_statistic.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_quota.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_dscp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_proto_sctp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_realm.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_time.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_netbios_ns.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_mark.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/xt_tcpmss.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/netrom/netrom.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_police.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_basic.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_route.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_teql.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_simple.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_nbyte.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_prio.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_atm.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_u32.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_hfsc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_rsvp6.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_rsvp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_nat.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_tbf.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_fw.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_red.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_text.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_dsmark.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_htb.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_sfq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_gred.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_cbq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_gact.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_ingress.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_mirred.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_skbedit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_cmp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_meta.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_pedit.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_flow.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_netem.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/em_u32.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/act_ipt.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_multiq.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/sch_drr.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sched/cls_tcindex.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sctp/sctp.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/phonet/pn_pep.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/phonet/phonet.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/sunrpc.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/auth_gss/rpcsec_gss_spkm3.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/auth_gss/auth_rpcgss.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/sunrpc/auth_gss/rpcsec_gss_krb5.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rxrpc/rxkad.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rxrpc/af-rxrpc.ko: Exec format error
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/nf_conntrack_pptp.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_lc.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_lblc.ko
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.32-26-generic/kernel/net/netfilter/ipvs/ip_vs_sed.ko
Failed to run depmod
dpkg: error processing linux-image-2.6.32-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.32-26-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
brady@brady-laptop:~$

---

### Post by plucky on 2011-01-26
What is your current kernel version?

Post output of ```
uname -a
```

There was a linux-image update today which took my kernel up to > 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux so hopefully you are on the 27-generic kernel.

Did you try to remove anything from the previous kernel? (2.6.32-26-generic)

> Running depmod.
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rose/rose.ko: Exec format error
WARNING: Can't read module /lib/modules/2.6.32-26-generic/kernel/net/rds/rds_rdma.ko: Exec format error

It is trying to do build modules for the previous kernel and failing.

You could try ```
sudo apt-get remove linux-image-2.6.32-26-generic
``` only if you are running the 27-generic kernel.

Good Luck

---

### Post by hunterkasy on 2011-01-26
brady@brady-laptop:~$ uname -a
Linux brady-laptop 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux
brady@brady-laptop:~$ 


I am going to try this command:

sudo apt-get remove linux-image-2.6.32-26-generic

because I am on the .27 kernel, I will post a update on if it works or not

---

### Post by hunterkasy on 2011-01-26
sudo apt-get remove linux-image-2.6.32-26-generic

that command fix my problem, I was able to update my computer and their was no more errors showing up,  I want to thank everyone that helped me

---

