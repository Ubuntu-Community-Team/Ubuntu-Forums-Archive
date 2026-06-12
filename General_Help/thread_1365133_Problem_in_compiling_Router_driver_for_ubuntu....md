---
title: "Problem in compiling Router driver for ubuntu..."
date: 2009-12-26
forum: General Help
---

### Post by emigrant on 2009-12-26
hi all,
i have a SpeedCom+ 4 port router,
im trying to use the router through USB as im having prob in connecting through ethernet. i tried to install the drivers according to the way mentioned in the manual.
but i keep getting error. below i have given the instruction given in the manual and the error i get.

please help me to solve this problem.
thank you very much.

```
Setup ADSL Router via USB Cable on Linux
This driver supports Linux-2.4 kernel.
Compiling the Driver
To compile the driver simply run make in "viking" directory. This will create binary driver with name VKGEther.
                    % make
Loading the module
To load the VKGEther module enter the following command as root in             directory "viking"
Syntax:
            % insmod ./VKGEther {Module Options}
Unloading the module
To unload an unused module:
            % rmmod VKGEther
You will need to exit or disconnect any program currently using the module before it unload. If the module was
configured for LAN, shutdown the ethernet interface:
            % ifconfig eth1 down
The ethernet interface associated with the VKGEther driver was "eth1" that's why interface name is eth1 in above
line.
LAN Configuration
To enable LAN traffic over the ethernet interface:
            % ifconfig eth1 192.168.1.200 up
You may also need to modify the netmask and route for the interface. Refer to the manual pages for ifconfig and
route for more information. To test the LAN connection is alive by pinging the remote side:
            % ping 192.168.1.1
To disconnect the LAN interface:
            % ifconfig eth1 down

```this is the error:

```
$ make
$ make
gcc -c -O2  -Wall -Wno-missing-braces -Wstrict-prototypes -fomit-frame-pointer -fno-strict-aliasing -pipe -fno-strength-reduce -mcpu=i486 -falign-loops=2 -falign-jumps=2 -falign-functions=2 -I/usr/src/linux/include -I./inc  -D__KERNEL__ -DMODULE  -Dlinux -DDBG=0 -o src/CDCEther.o src/CDCEther.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
src/CDCEther.c:23:24: error: linux/slab.h: No such file or directory
src/CDCEther.c:24:24: error: linux/init.h: No such file or directory
src/CDCEther.c:25:25: error: linux/delay.h: No such file or directory
In file included from /usr/include/linux/socket.h:23,
                 from /usr/include/linux/if.h:23,
                 from /usr/include/linux/netdevice.h:28,
                 from src/CDCEther.c:26:
/usr/include/linux/uio.h:37: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iov_length’
/usr/include/linux/uio.h:47: error: expected declaration specifiers or ‘...’ before ‘size_t’
src/CDCEther.c:27:31: error: linux/etherdevice.h: No such file or directory
src/CDCEther.c:28:23: error: linux/usb.h: No such file or directory
src/CDCEther.c:29:26: error: linux/module.h: No such file or directory
src/CDCEther.c:31:25: error: asm/uaccess.h: No such file or directory
In file included from src/CDCEther.c:32:
./inc/CDCEther.h:79:41: error: missing binary operator before token "("
In file included from src/CDCEther.c:32:
./inc/CDCEther.h:87: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘USB_CTRLREQUEST’
./inc/CDCEther.h:126: error: expected specifier-qualifier-list before ‘USB_CTRLREQUEST’
src/CDCEther.c:38: error: array type has incomplete element type
src/CDCEther.c:39: warning: implicit declaration of function ‘USB_DEVICE’
src/CDCEther.c:58: warning: ‘struct urb’ declared inside parameter list
src/CDCEther.c:58: warning: its scope is only this definition or declaration, which is probably not what you want
src/CDCEther.c: In function ‘read_bulk_callback’:
src/CDCEther.c:60: error: dereferencing pointer to incomplete type
src/CDCEther.c:64: error: dereferencing pointer to incomplete type
src/CDCEther.c:75: warning: implicit declaration of function ‘dbg’
src/CDCEther.c:83: warning: implicit declaration of function ‘netif_device_present’
src/CDCEther.c:98: error: dereferencing pointer to incomplete type
src/CDCEther.c:99: error: ‘USB_ST_NOERROR’ undeclared (first use in this function)
src/CDCEther.c:99: error: (Each undeclared identifier is reported only once
src/CDCEther.c:99: error: for each function it appears in.)
src/CDCEther.c:101: error: ‘USB_ST_NORESPONSE’ undeclared (first use in this function)
src/CDCEther.c:108: error: dereferencing pointer to incomplete type
src/CDCEther.c:108: error: dereferencing pointer to incomplete type
src/CDCEther.c:125: error: ‘ether_dev_t’ has no member named ‘rx_buff’
src/CDCEther.c:126: error: ‘ether_dev_t’ has no member named ‘rx_buff’
src/CDCEther.c:129: error: ‘ether_dev_t’ has no member named ‘rxsequence’
src/CDCEther.c:129: error: ‘ether_dev_t’ has no member named ‘rx_buff’
src/CDCEther.c:134: error: ‘ether_dev_t’ has no member named ‘rx_out_of_seq’
src/CDCEther.c:136: error: ‘ether_dev_t’ has no member named ‘rxsequence’
src/CDCEther.c:136: error: ‘ether_dev_t’ has no member named ‘rx_buff’
src/CDCEther.c:140: error: ‘ether_dev_t’ has no member named ‘rx_out_of_seq’
src/CDCEther.c:145: error: ‘ether_dev_t’ has no member named ‘rx_out_of_seq’
src/CDCEther.c:147: warning: implicit declaration of function ‘memcpy’
src/CDCEther.c:147: warning: incompatible implicit declaration of built-in function ‘memcpy’
src/CDCEther.c:147: error: ‘ether_dev_t’ has no member named ‘rx_buff’
src/CDCEther.c:148: error: ‘ether_dev_t’ has no member named ‘rx_buff’
src/CDCEther.c:157: error: ‘ether_dev_t’ has no member named ‘rxsequence’
src/CDCEther.c:168: warning: implicit declaration of function ‘dev_alloc_skb’
src/CDCEther.c:168: warning: assignment makes pointer from integer without a cast
src/CDCEther.c:175: error: dereferencing pointer to incomplete type
src/CDCEther.c:178: warning: implicit declaration of function ‘eth_copy_and_sum’
src/CDCEther.c:178: error: ‘ether_dev_t’ has no member named ‘rx_buff’
src/CDCEther.c:181: warning: implicit declaration of function ‘skb_put’
src/CDCEther.c:183: error: dereferencing pointer to incomplete type
src/CDCEther.c:183: warning: implicit declaration of function ‘eth_type_trans’
src/CDCEther.c:186: warning: implicit declaration of function ‘netif_rx’
src/CDCEther.c:194: warning: implicit declaration of function ‘FILL_BULK_URB’
src/CDCEther.c:194: error: ‘ether_dev_t’ has no member named ‘rx_urb’
src/CDCEther.c:195: warning: implicit declaration of function ‘usb_rcvbulkpipe’
src/CDCEther.c:196: error: ‘ether_dev_t’ has no member named ‘rx_buff’
src/CDCEther.c:199: error: ‘ether_dev_t’ has no member named ‘rx_urb’
src/CDCEther.c:199: error: ‘USB_QUEUE_BULK’ undeclared (first use in this function)
src/CDCEther.c:203: warning: implicit declaration of function ‘usb_submit_urb’
src/CDCEther.c:203: error: ‘ether_dev_t’ has no member named ‘rx_urb’
src/CDCEther.c:204: warning: implicit declaration of function ‘warn’
src/CDCEther.c: At top level:
src/CDCEther.c:213: warning: ‘struct urb’ declared inside parameter list
src/CDCEther.c: In function ‘write_bulk_callback’:
src/CDCEther.c:215: error: dereferencing pointer to incomplete type
src/CDCEther.c:220: warning: implicit declaration of function ‘err’
src/CDCEther.c:232: error: dereferencing pointer to incomplete type
src/CDCEther.c:233: error: dereferencing pointer to incomplete type
src/CDCEther.c:233: error: dereferencing pointer to incomplete type
src/CDCEther.c:238: error: dereferencing pointer to incomplete type
src/CDCEther.c:238: error: ‘jiffies’ undeclared (first use in this function)
src/CDCEther.c:240: warning: implicit declaration of function ‘netif_wake_queue’
src/CDCEther.c: At top level:
src/CDCEther.c:243: warning: ‘struct urb’ declared inside parameter list
src/CDCEther.c: In function ‘process_notification’:
src/CDCEther.c:249: error: dereferencing pointer to incomplete type
src/CDCEther.c:252: error: dereferencing pointer to incomplete type
src/CDCEther.c:253: error: dereferencing pointer to incomplete type
src/CDCEther.c:257: error: dereferencing pointer to incomplete type
src/CDCEther.c:268: warning: implicit declaration of function ‘printk’
src/CDCEther.c:268: error: ‘KERN_INFO’ undeclared (first use in this function)
src/CDCEther.c:268: error: expected ‘)’ before string constant
src/CDCEther.c:269: error: expected ‘)’ before string constant
src/CDCEther.c:273: error: expected ‘)’ before string constant
src/CDCEther.c:274: error: expected ‘)’ before string constant
src/CDCEther.c:288: error: dereferencing pointer to incomplete type
src/CDCEther.c:290: error: dereferencing pointer to incomplete type
src/CDCEther.c: At top level:
src/CDCEther.c:311: warning: ‘struct urb’ declared inside parameter list
src/CDCEther.c: In function ‘intr_callback’:
src/CDCEther.c:313: error: dereferencing pointer to incomplete type
src/CDCEther.c:320: error: dereferencing pointer to incomplete type
src/CDCEther.c:321: error: ‘USB_ST_NOERROR’ undeclared (first use in this function)
src/CDCEther.c:323: error: ‘USB_ST_URB_KILLED’ undeclared (first use in this function)
src/CDCEther.c:326: warning: implicit declaration of function ‘info’
src/CDCEther.c:326: error: dereferencing pointer to incomplete type
src/CDCEther.c:331: error: dereferencing pointer to incomplete type
src/CDCEther.c:332: warning: passing argument 1 of ‘process_notification’ from incompatible pointer type
src/CDCEther.c: At top level:
src/CDCEther.c:337: warning: ‘struct urb’ declared inside parameter list
src/CDCEther.c: In function ‘setpktfilter_done’:
src/CDCEther.c:339: error: dereferencing pointer to incomplete type
src/CDCEther.c:343: error: dereferencing pointer to incomplete type
src/CDCEther.c:344: error: ‘USB_ST_NOERROR’ undeclared (first use in this function)
src/CDCEther.c:346: error: ‘USB_ST_URB_KILLED’ undeclared (first use in this function)
src/CDCEther.c:349: error: dereferencing pointer to incomplete type
src/CDCEther.c:351: error: ‘ether_dev_t’ has no member named ‘ctrl_pending’
src/CDCEther.c: In function ‘CDC_SetEthernetPacketFilter’:
src/CDCEther.c:356: error: ‘USB_CTRLREQUEST’ undeclared (first use in this function)
src/CDCEther.c:356: error: ‘dr’ undeclared (first use in this function)
src/CDCEther.c:356: error: ‘ether_dev_t’ has no member named ‘ctrl_dr’
src/CDCEther.c:359: error: ‘ether_dev_t’ has no member named ‘ctrl_pending’
src/CDCEther.c:361: error: ‘USB_TYPE_CLASS’ undeclared (first use in this function)
src/CDCEther.c:361: error: ‘USB_DIR_OUT’ undeclared (first use in this function)
src/CDCEther.c:361: error: ‘USB_RECIP_INTERFACE’ undeclared (first use in this function)
src/CDCEther.c:363: warning: implicit declaration of function ‘cpu_to_le16’
src/CDCEther.c:364: error: ‘u16’ undeclared (first use in this function)
src/CDCEther.c:364: error: expected ‘)’ before ‘ether_dev’
src/CDCEther.c:367: warning: implicit declaration of function ‘usb_fill_control_urb’
src/CDCEther.c:367: error: ‘ether_dev_t’ has no member named ‘ctrl_urb’
src/CDCEther.c:369: warning: implicit declaration of function ‘usb_sndctrlpipe’
src/CDCEther.c:375: error: ‘ether_dev_t’ has no member named ‘ctrl_urb’
src/CDCEther.c:378: error: ‘ether_dev_t’ has no member named ‘ctrl_pending’
src/CDCEther.c: In function ‘CDCEther_StartInt’:
src/CDCEther.c:391: warning: implicit declaration of function ‘FILL_INT_URB’
src/CDCEther.c:391: error: ‘ether_dev_t’ has no member named ‘intr_urb’
src/CDCEther.c:392: warning: implicit declaration of function ‘usb_rcvintpipe’
src/CDCEther.c:393: error: ‘ether_dev_t’ has no member named ‘intr_buff’
src/CDCEther.c:396: error: ‘ether_dev_t’ has no member named ‘intr_urb’
src/CDCEther.c: In function ‘CDCEther_tx_timeout’:
src/CDCEther.c:409: error: dereferencing pointer to incomplete type
src/CDCEther.c:420: error: dereferencing pointer to incomplete type
src/CDCEther.c:423: error: ‘ether_dev_t’ has no member named ‘tx_urb’
src/CDCEther.c:423: error: ‘USB_ASYNC_UNLINK’ undeclared (first use in this function)
src/CDCEther.c:424: warning: implicit declaration of function ‘usb_unlink_urb’
src/CDCEther.c:424: error: ‘ether_dev_t’ has no member named ‘tx_urb’
src/CDCEther.c: At top level:
src/CDCEther.c:430: warning: ‘struct sk_buff’ declared inside parameter list
src/CDCEther.c: In function ‘CDCEther_start_xmit’:
src/CDCEther.c:432: error: dereferencing pointer to incomplete type
src/CDCEther.c:443: warning: implicit declaration of function ‘netif_stop_queue’
src/CDCEther.c:445: error: dereferencing pointer to incomplete type
src/CDCEther.c:473: error: ‘ether_dev_t’ has no member named ‘tx_buff’
src/CDCEther.c:475: error: ‘ether_dev_t’ has no member named ‘tx_buff’
src/CDCEther.c:477: error: ‘ether_dev_t’ has no member named ‘tx_buff’
src/CDCEther.c:477: error: ‘ether_dev_t’ has no member named ‘txsequence’
src/CDCEther.c:480: warning: incompatible implicit declaration of built-in function ‘memcpy’
src/CDCEther.c:480: error: ‘ether_dev_t’ has no member named ‘tx_buff’
src/CDCEther.c:481: error: dereferencing pointer to incomplete type
src/CDCEther.c:485: error: ‘ether_dev_t’ has no member named ‘txsequence’
src/CDCEther.c:485: error: ‘ether_dev_t’ has no member named ‘txsequence’
src/CDCEther.c:499: warning: implicit declaration of function ‘memset’
src/CDCEther.c:499: warning: incompatible implicit declaration of built-in function ‘memset’
src/CDCEther.c:499: error: ‘ether_dev_t’ has no member named ‘tx_buff’
src/CDCEther.c:504: error: ‘ether_dev_t’ has no member named ‘tx_urb’
src/CDCEther.c:505: warning: implicit declaration of function ‘usb_sndbulkpipe’
src/CDCEther.c:506: error: ‘ether_dev_t’ has no member named ‘tx_buff’
src/CDCEther.c:509: error: ‘ether_dev_t’ has no member named ‘tx_urb’
src/CDCEther.c:509: error: ‘USB_QUEUE_BULK’ undeclared (first use in this function)
src/CDCEther.c:512: error: ‘ether_dev_t’ has no member named ‘tx_urb’
src/CDCEther.c:520: warning: implicit declaration of function ‘netif_start_queue’
src/CDCEther.c:525: error: dereferencing pointer to incomplete type
src/CDCEther.c:527: error: dereferencing pointer to incomplete type
src/CDCEther.c:527: error: ‘jiffies’ undeclared (first use in this function)
src/CDCEther.c:532: warning: implicit declaration of function ‘dev_kfree_skb’
src/CDCEther.c: In function ‘CDCEther_netdev_stats’:
src/CDCEther.c:581: error: dereferencing pointer to incomplete type
src/CDCEther.c: In function ‘CDCEther_open’:
src/CDCEther.c:586: error: dereferencing pointer to incomplete type
src/CDCEther.c:600: error: ‘ether_dev_t’ has no member named ‘rx_urb’
src/CDCEther.c:602: error: ‘ether_dev_t’ has no member named ‘rx_buff’
src/CDCEther.c:606: error: ‘ether_dev_t’ has no member named ‘rx_urb’
src/CDCEther.c:624: warning: implicit declaration of function ‘usb_inc_dev_use’
src/CDCEther.c: In function ‘CDCEther_close’:
src/CDCEther.c:632: error: dereferencing pointer to incomplete type
src/CDCEther.c:646: error: ‘ether_dev_t’ has no member named ‘rx_urb’
src/CDCEther.c:652: error: ‘ether_dev_t’ has no member named ‘tx_urb’
src/CDCEther.c:654: error: ‘ether_dev_t’ has no member named ‘intr_urb’
src/CDCEther.c:656: warning: implicit declaration of function ‘usb_dec_dev_use’
src/CDCEther.c:658: warning: implicit declaration of function ‘set_current_state’
src/CDCEther.c:658: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
src/CDCEther.c:659: warning: implicit declaration of function ‘in_interrupt’
src/CDCEther.c:660: warning: implicit declaration of function ‘schedule_timeout’
src/CDCEther.c:660: error: ‘HZ’ undeclared (first use in this function)
src/CDCEther.c: In function ‘netdev_ethtool_ioctl’:
src/CDCEther.c:668: error: ‘u32’ undeclared (first use in this function)
src/CDCEther.c:668: error: expected ‘;’ before ‘ethcmd’
src/CDCEther.c:672: warning: implicit declaration of function ‘copy_from_user’
src/CDCEther.c:672: error: ‘ethcmd’ undeclared (first use in this function)
src/CDCEther.c:673: error: ‘EFAULT’ undeclared (first use in this function)
src/CDCEther.c:678: warning: implicit declaration of function ‘strncpy’
src/CDCEther.c:678: warning: incompatible implicit declaration of built-in function ‘strncpy’
src/CDCEther.c:679: warning: implicit declaration of function ‘copy_to_user’
src/CDCEther.c:686: error: ‘EOPNOTSUPP’ undeclared (first use in this function)
src/CDCEther.c: In function ‘CDCEther_ioctl’:
src/CDCEther.c:702: error: ‘EOPNOTSUPP’ undeclared (first use in this function)
src/CDCEther.c: In function ‘CDCEther_set_multicast’:
src/CDCEther.c:715: error: dereferencing pointer to incomplete type
src/CDCEther.c:724: error: dereferencing pointer to incomplete type
src/CDCEther.c:733: error: dereferencing pointer to incomplete type
src/CDCEther.c:735: error: dereferencing pointer to incomplete type
src/CDCEther.c:741: error: dereferencing pointer to incomplete type
src/CDCEther.c:743: error: dereferencing pointer to incomplete type
src/CDCEther.c:751: error: dereferencing pointer to incomplete type
src/CDCEther.c: In function ‘find_and_parse_ethernet_class_information’:
src/CDCEther.c:1012: error: dereferencing pointer to incomplete type
src/CDCEther.c:1013: error: dereferencing pointer to incomplete type
src/CDCEther.c:1014: error: dereferencing pointer to incomplete type
src/CDCEther.c:1019: error: dereferencing pointer to incomplete type
src/CDCEther.c:1021: error: dereferencing pointer to incomplete type
src/CDCEther.c:1021: error: dereferencing pointer to incomplete type
src/CDCEther.c:1022: error: dereferencing pointer to incomplete type
src/CDCEther.c:1027: error: dereferencing pointer to incomplete type
src/CDCEther.c:1027: error: dereferencing pointer to incomplete type
src/CDCEther.c: In function ‘get_data_interface_endpoints’:
src/CDCEther.c:1047: error: dereferencing pointer to incomplete type
src/CDCEther.c:1048: error: dereferencing pointer to incomplete type
src/CDCEther.c:1049: error: dereferencing pointer to incomplete type
src/CDCEther.c:1056: error: dereferencing pointer to incomplete type
src/CDCEther.c:1057: error: dereferencing pointer to incomplete type
src/CDCEther.c:1060: error: dereferencing pointer to incomplete type
src/CDCEther.c:1061: error: dereferencing pointer to incomplete type
src/CDCEther.c:1062: error: dereferencing pointer to incomplete type
src/CDCEther.c:1072: error: dereferencing pointer to incomplete type
src/CDCEther.c:1074: error: dereferencing pointer to incomplete type
src/CDCEther.c:1077: error: dereferencing pointer to incomplete type
src/CDCEther.c:1078: error: dereferencing pointer to incomplete type
src/CDCEther.c:1082: error: dereferencing pointer to incomplete type
src/CDCEther.c:1084: error: dereferencing pointer to incomplete type
src/CDCEther.c:1087: error: dereferencing pointer to incomplete type
src/CDCEther.c:1088: error: dereferencing pointer to incomplete type
src/CDCEther.c: In function ‘verify_ethernet_data_interface’:
src/CDCEther.c:1113: error: dereferencing pointer to incomplete type
src/CDCEther.c:1114: error: dereferencing pointer to incomplete type
src/CDCEther.c:1124: error: dereferencing pointer to incomplete type
src/CDCEther.c:1125: error: dereferencing pointer to incomplete type
src/CDCEther.c:1128: error: dereferencing pointer to incomplete type
src/CDCEther.c:1129: error: dereferencing pointer to incomplete type
src/CDCEther.c:1130: error: dereferencing pointer to incomplete type
src/CDCEther.c:1131: error: dereferencing pointer to incomplete type
src/CDCEther.c:1138: error: dereferencing pointer to incomplete type
src/CDCEther.c:1140: error: dereferencing pointer to incomplete type
src/CDCEther.c:1146: error: dereferencing pointer to incomplete type
src/CDCEther.c:1151: error: dereferencing pointer to incomplete type
src/CDCEther.c:1153: error: dereferencing pointer to incomplete type
src/CDCEther.c: In function ‘find_ethernet_comm_interface’:
src/CDCEther.c:1173: error: dereferencing pointer to incomplete type
src/CDCEther.c:1177: error: dereferencing pointer to incomplete type
src/CDCEther.c:1178: error: dereferencing pointer to incomplete type
src/CDCEther.c:1181: error: dereferencing pointer to incomplete type
src/CDCEther.c:1182: error: dereferencing pointer to incomplete type
src/CDCEther.c:1187: error: dereferencing pointer to incomplete type
src/CDCEther.c:1189: error: dereferencing pointer to incomplete type
src/CDCEther.c: In function ‘find_valid_configuration’:
src/CDCEther.c:1230: error: dereferencing pointer to incomplete type
src/CDCEther.c:1231: error: dereferencing pointer to incomplete type
src/CDCEther.c:1238: error: dereferencing pointer to incomplete type
src/CDCEther.c: At top level:
src/CDCEther.c:1259: warning: ‘struct usb_config_descriptor’ declared inside parameter list
src/CDCEther.c: In function ‘check_for_claimed_interfaces’:
src/CDCEther.c:1266: error: dereferencing pointer to incomplete type
src/CDCEther.c:1267: error: dereferencing pointer to incomplete type
src/CDCEther.c:1268: warning: implicit declaration of function ‘usb_interface_claimed’
src/CDCEther.c: In function ‘set_ethernet_addr’:
src/CDCEther.c:1316: warning: implicit declaration of function ‘usb_string’
src/CDCEther.c:1343: warning: incompatible implicit declaration of built-in function ‘memcpy’
src/CDCEther.c:1343: error: dereferencing pointer to incomplete type
src/CDCEther.c: In function ‘log_device_info’:
src/CDCEther.c:1366: error: dereferencing pointer to incomplete type
src/CDCEther.c:1375: error: dereferencing pointer to incomplete type
src/CDCEther.c:1384: error: dereferencing pointer to incomplete type
src/CDCEther.c:1393: error: dereferencing pointer to incomplete type
src/CDCEther.c:1397: error: dereferencing pointer to incomplete type
src/CDCEther.c: In function ‘CDCEther_probe’:
src/CDCEther.c:1420: error: dereferencing pointer to incomplete type
src/CDCEther.c:1430: warning: implicit declaration of function ‘kmalloc’
src/CDCEther.c:1430: error: ‘GFP_KERNEL’ undeclared (first use in this function)
src/CDCEther.c:1430: warning: assignment makes pointer from integer without a cast
src/CDCEther.c:1436: warning: incompatible implicit declaration of built-in function ‘memset’
src/CDCEther.c:1442: warning: implicit declaration of function ‘kfree’
src/CDCEther.c:1448: warning: implicit declaration of function ‘usb_set_configuration’
src/CDCEther.c:1456: warning: implicit declaration of function ‘usb_set_interface’
src/CDCEther.c:1496: warning: implicit declaration of function ‘usb_clear_halt’
src/CDCEther.c:1506: warning: implicit declaration of function ‘init_etherdev’
src/CDCEther.c:1506: warning: assignment makes pointer from integer without a cast
src/CDCEther.c:1517: error: dereferencing pointer to incomplete type
src/CDCEther.c:1518: warning: implicit declaration of function ‘SET_MODULE_OWNER’
src/CDCEther.c:1519: error: dereferencing pointer to incomplete type
src/CDCEther.c:1520: error: dereferencing pointer to incomplete type
src/CDCEther.c:1521: error: dereferencing pointer to incomplete type
src/CDCEther.c:1521: error: ‘HZ’ undeclared (first use in this function)
src/CDCEther.c:1522: error: dereferencing pointer to incomplete type
src/CDCEther.c:1523: error: dereferencing pointer to incomplete type
src/CDCEther.c:1524: error: dereferencing pointer to incomplete type
src/CDCEther.c:1525: error: dereferencing pointer to incomplete type
src/CDCEther.c:1526: error: dereferencing pointer to incomplete type
src/CDCEther.c:1527: error: dereferencing pointer to incomplete type
src/CDCEther.c:1531: error: ‘ether_dev_t’ has no member named ‘ctrl_pending’
src/CDCEther.c:1540: warning: implicit declaration of function ‘usb_driver_claim_interface’
src/CDCEther.c:1541: error: dereferencing pointer to incomplete type
src/CDCEther.c: In function ‘CDCEther_disconnect’:
src/CDCEther.c:1574: warning: implicit declaration of function ‘unregister_netdev’
src/CDCEther.c:1583: warning: implicit declaration of function ‘usb_driver_release_interface’
src/CDCEther.c:1584: error: dereferencing pointer to incomplete type
src/CDCEther.c:1588: error: dereferencing pointer to incomplete type
src/CDCEther.c: At top level:
src/CDCEther.c:1601: error: variable ‘CDCEther_driver’ has initializer but incomplete type
src/CDCEther.c:1602: error: unknown field ‘name’ specified in initializer
src/CDCEther.c:1602: warning: excess elements in struct initializer
src/CDCEther.c:1602: warning: (near initialization for ‘CDCEther_driver’)
src/CDCEther.c:1603: error: unknown field ‘probe’ specified in initializer
src/CDCEther.c:1603: warning: excess elements in struct initializer
src/CDCEther.c:1603: warning: (near initialization for ‘CDCEther_driver’)
src/CDCEther.c:1604: error: unknown field ‘disconnect’ specified in initializer
src/CDCEther.c:1604: warning: excess elements in struct initializer
src/CDCEther.c:1604: warning: (near initialization for ‘CDCEther_driver’)
src/CDCEther.c:1605: error: unknown field ‘id_table’ specified in initializer
src/CDCEther.c:1605: warning: excess elements in struct initializer
src/CDCEther.c:1605: warning: (near initialization for ‘CDCEther_driver’)
src/CDCEther.c:1612: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CDCEther_init’
src/CDCEther.c:1619: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘CDCEther_exit’
src/CDCEther.c:1628: warning: data definition has no type or storage class
src/CDCEther.c:1628: warning: type defaults to ‘int’ in declaration of ‘module_init’
src/CDCEther.c:1628: warning: parameter names (without types) in function declaration
src/CDCEther.c:1629: warning: data definition has no type or storage class
src/CDCEther.c:1629: warning: type defaults to ‘int’ in declaration of ‘module_exit’
src/CDCEther.c:1629: warning: parameter names (without types) in function declaration
src/CDCEther.c:1631: error: expected declaration specifiers or ‘...’ before string constant
src/CDCEther.c:1631: warning: data definition has no type or storage class
src/CDCEther.c:1631: warning: type defaults to ‘int’ in declaration of ‘MODULE_AUTHOR’
src/CDCEther.c:1631: warning: function declaration isn’t a prototype
src/CDCEther.c:1632: error: expected declaration specifiers or ‘...’ before string constant
src/CDCEther.c:1632: warning: data definition has no type or storage class
src/CDCEther.c:1632: warning: type defaults to ‘int’ in declaration of ‘MODULE_DESCRIPTION’
src/CDCEther.c:1632: warning: function declaration isn’t a prototype
src/CDCEther.c:1633: error: expected declaration specifiers or ‘...’ before string constant
src/CDCEther.c:1633: warning: data definition has no type or storage class
src/CDCEther.c:1633: warning: type defaults to ‘int’ in declaration of ‘MODULE_LICENSE’
src/CDCEther.c:1633: warning: function declaration isn’t a prototype
src/CDCEther.c:1635: error: expected ‘)’ before string constant
src/CDCEther.c:1636: error: expected ‘)’ before string constant
src/CDCEther.c:1637: error: expected ‘)’ before string constant
src/CDCEther.c:1638: error: expected ‘)’ before string constant
src/CDCEther.c:1640: warning: data definition has no type or storage class
src/CDCEther.c:1640: warning: type defaults to ‘int’ in declaration of ‘MODULE_DEVICE_TABLE’
src/CDCEther.c:1640: warning: parameter names (without types) in function declaration
make: *** [src/CDCEther.o] Error 1

```

---

### Post by audiomick on 2009-12-26
Hi. In the instructions for the driver, it says it supports the 2.4 kernel. Could it be that you have a 2.6?

---

### Post by emigrant on 2009-12-26
yeah. im having 2.6. that means i should downgrade to 2.4?
how to make it in 2.6 please :confused:

---

