---
title: "Help Installing ftdi Drivers"
date: 2010-01-27
forum: General Help
---

### Post by gunjannigam on 2010-01-27
Hi,
I am new to this Ubuntu and this forum. I am working with Ubuntu 9.04. I want to install the ftdi drivers in Ubuntu from [http://www.ftdichip.com/Drivers/VCP.htm](http://www.ftdichip.com/Drivers/VCP.htm). I unzipped the tar package and used make command in the terminal, but it gives too many erros and warnings. Below are the errors which are displayed on terminal.  
ftdi_sio.c:834: error: dereferencing pointer to incomplete type
ftdi_sio.c:835: error: dereferencing pointer to incomplete type
ftdi_sio.c: At top level:
ftdi_sio.c:846: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:846: error: conflicting types for ‘get_ftdi_divisor’
ftdi_sio.c:811: error: previous declaration of ‘get_ftdi_divisor’ was here
ftdi_sio.c: In function ‘get_ftdi_divisor’:
ftdi_sio.c:848: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:878: warning: implicit declaration of function ‘tty_get_baud_rate’
ftdi_sio.c:878: error: dereferencing pointer to incomplete type
ftdi_sio.c:957: warning: implicit declaration of function ‘tty_encode_baud_rate’
ftdi_sio.c:957: error: dereferencing pointer to incomplete type
ftdi_sio.c: At top level:
ftdi_sio.c:962: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
ftdi_sio.c:979: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
ftdi_sio.c:1040: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c: In function ‘ftdi_determine_type’:
ftdi_sio.c:1042: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1043: error: dereferencing pointer to incomplete type
ftdi_sio.c:1044: error: dereferencing pointer to incomplete type
ftdi_sio.c:1052: warning: implicit declaration of function ‘le16_to_cpu’
ftdi_sio.c:1052: error: dereferencing pointer to incomplete type
ftdi_sio.c:1053: error: dereferencing pointer to incomplete type
ftdi_sio.c:1072: error: dereferencing pointer to incomplete type
ftdi_sio.c:1074: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c:1076: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c:1078: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c:1080: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c:1105: warning: implicit declaration of function ‘info’
ftdi_sio.c: At top level:
ftdi_sio.c:1112: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c: In function ‘ftdi_set_max_packet_size’:
ftdi_sio.c:1114: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1115: error: dereferencing pointer to incomplete type
ftdi_sio.c:1117: error: dereferencing pointer to incomplete type
ftdi_sio.c:1118: error: dereferencing pointer to incomplete type
ftdi_sio.c:1123: error: dereferencing pointer to incomplete type
ftdi_sio.c:1133: error: dereferencing pointer to incomplete type
ftdi_sio.c:1134: error: dereferencing pointer to incomplete type
ftdi_sio.c:1135: error: dereferencing pointer to incomplete type
ftdi_sio.c:1136: error: dereferencing pointer to incomplete type
ftdi_sio.c:1136: warning: implicit declaration of function ‘cpu_to_le16’
ftdi_sio.c:1142: error: ‘struct ftdi_private’ has no member named ‘max_packet_size’
ftdi_sio.c:1142: error: dereferencing pointer to incomplete type
ftdi_sio.c:1144: error: ‘struct ftdi_private’ has no member named ‘max_packet_size’
ftdi_sio.c: At top level:
ftdi_sio.c:1154: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘show_latency_timer’
ftdi_sio.c:1180: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘store_latency_timer’
ftdi_sio.c:1209: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘store_event_char’
ftdi_sio.c:1236: error: expected ‘)’ before ‘|’ token
ftdi_sio.c:1237: error: expected ‘)’ before ‘(’ token
ftdi_sio.c:1239: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c: In function ‘create_sysfs_attrs’:
ftdi_sio.c:1241: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1250: warning: implicit declaration of function ‘device_create_file’
ftdi_sio.c:1250: error: dereferencing pointer to incomplete type
ftdi_sio.c:1250: error: ‘dev_attr_event_char’ undeclared (first use in this function)
ftdi_sio.c:1257: error: dereferencing pointer to incomplete type
ftdi_sio.c:1258: error: ‘dev_attr_latency_timer’ undeclared (first use in this function)
ftdi_sio.c: At top level:
ftdi_sio.c:1264: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c: In function ‘remove_sysfs_attrs’:
ftdi_sio.c:1266: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1272: warning: implicit declaration of function ‘device_remove_file’
ftdi_sio.c:1272: error: dereferencing pointer to incomplete type
ftdi_sio.c:1272: error: ‘dev_attr_event_char’ undeclared (first use in this function)
ftdi_sio.c:1278: error: dereferencing pointer to incomplete type
ftdi_sio.c:1278: error: ‘dev_attr_latency_timer’ undeclared (first use in this function)
ftdi_sio.c: At top level:
ftdi_sio.c:1291: warning: ‘struct usb_serial’ declared inside parameter list
ftdi_sio.c:1291: error: conflicting types for ‘ftdi_sio_probe’
ftdi_sio.c:620: error: previous declaration of ‘ftdi_sio_probe’ was here
ftdi_sio.c: In function ‘ftdi_sio_probe’:
ftdi_sio.c:1293: error: dereferencing pointer to incomplete type
ftdi_sio.c:1296: warning: passing argument 1 of ‘quirk->probe’ from incompatible pointer type
ftdi_sio.c:1301: warning: implicit declaration of function ‘usb_set_serial_data’
ftdi_sio.c:1301: error: dereferencing pointer to incomplete type
ftdi_sio.c: At top level:
ftdi_sio.c:1306: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:1306: error: conflicting types for ‘ftdi_sio_port_probe’
ftdi_sio.c:622: error: previous declaration of ‘ftdi_sio_port_probe’ was here
ftdi_sio.c: In function ‘ftdi_sio_port_probe’:
ftdi_sio.c:1309: warning: implicit declaration of function ‘usb_get_serial_data’
ftdi_sio.c:1309: error: dereferencing pointer to incomplete type
ftdi_sio.c:1309: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1314: warning: implicit declaration of function ‘kzalloc’
ftdi_sio.c:1314: error: ‘GFP_KERNEL’ undeclared (first use in this function)
ftdi_sio.c:1314: warning: assignment makes pointer from integer without a cast
ftdi_sio.c:1320: warning: implicit declaration of function ‘spin_lock_init’
ftdi_sio.c:1320: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:1321: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1322: warning: implicit declaration of function ‘init_waitqueue_head’
ftdi_sio.c:1322: error: ‘struct ftdi_private’ has no member named ‘delta_msr_wait’
ftdi_sio.c:1331: error: dereferencing pointer to incomplete type
ftdi_sio.c:1332: error: dereferencing pointer to incomplete type
ftdi_sio.c:1333: error: dereferencing pointer to incomplete type
ftdi_sio.c:1337: error: dereferencing pointer to incomplete type
ftdi_sio.c:1338: error: dereferencing pointer to incomplete type
ftdi_sio.c:1338: error: dereferencing pointer to incomplete type
ftdi_sio.c:1339: error: dereferencing pointer to incomplete type
ftdi_sio.c:1342: warning: implicit declaration of function ‘INIT_DELAYED_WORK’
ftdi_sio.c:1342: error: ‘struct ftdi_private’ has no member named ‘rx_work’
ftdi_sio.c:1343: error: ‘struct ftdi_private’ has no member named ‘port’
ftdi_sio.c:1346: error: dereferencing pointer to incomplete type
ftdi_sio.c:1347: warning: implicit declaration of function ‘usb_free_urb’
ftdi_sio.c:1347: error: dereferencing pointer to incomplete type
ftdi_sio.c:1348: error: dereferencing pointer to incomplete type
ftdi_sio.c:1350: error: dereferencing pointer to incomplete type
ftdi_sio.c:1351: error: dereferencing pointer to incomplete type
ftdi_sio.c:1353: warning: implicit declaration of function ‘usb_set_serial_port_data’
ftdi_sio.c:1355: warning: passing argument 1 of ‘ftdi_determine_type’ from incompatible pointer type
ftdi_sio.c:1356: warning: passing argument 1 of ‘ftdi_set_max_packet_size’ from incompatible pointer type
ftdi_sio.c:1357: warning: passing argument 1 of ‘create_sysfs_attrs’ from incompatible pointer type
ftdi_sio.c: In function ‘ftdi_USB_UIRT_setup’:
ftdi_sio.c:1370: error: ‘struct ftdi_private’ has no member named ‘force_baud’
ftdi_sio.c: In function ‘ftdi_HE_TIRA1_setup’:
ftdi_sio.c:1381: error: ‘struct ftdi_private’ has no member named ‘force_baud’
ftdi_sio.c:1382: error: ‘struct ftdi_private’ has no member named ‘force_rtscts’
ftdi_sio.c: At top level:
ftdi_sio.c:1389: warning: ‘struct usb_serial’ declared inside parameter list
ftdi_sio.c:1389: error: conflicting types for ‘ftdi_olimex_probe’
ftdi_sio.c:316: error: previous declaration of ‘ftdi_olimex_probe’ was here
ftdi_sio.c: In function ‘ftdi_olimex_probe’:
ftdi_sio.c:1391: error: dereferencing pointer to incomplete type
ftdi_sio.c:1392: error: dereferencing pointer to incomplete type
ftdi_sio.c:1396: error: dereferencing pointer to incomplete type
ftdi_sio.c: At top level:
ftdi_sio.c:1411: warning: ‘struct usb_serial’ declared inside parameter list
ftdi_sio.c:1411: error: conflicting types for ‘ftdi_shutdown’
ftdi_sio.c:621: error: previous declaration of ‘ftdi_shutdown’ was here
ftdi_sio.c:1416: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:1416: error: conflicting types for ‘ftdi_sio_port_remove’
ftdi_sio.c:623: error: previous declaration of ‘ftdi_sio_port_remove’ was here
ftdi_sio.c: In function ‘ftdi_sio_port_remove’:
ftdi_sio.c:1418: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1422: warning: passing argument 1 of ‘remove_sysfs_attrs’ from incompatible pointer type
ftdi_sio.c: At top level:
ftdi_sio.c:1436: warning: ‘struct file’ declared inside parameter list
ftdi_sio.c:1436: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:1436: error: conflicting types for ‘ftdi_open’
ftdi_sio.c:624: error: previous declaration of ‘ftdi_open’ was here
ftdi_sio.c: In function ‘ftdi_open’:
ftdi_sio.c:1438: error: dereferencing pointer to incomplete type
ftdi_sio.c:1439: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1447: warning: implicit declaration of function ‘spin_lock_irqsave’
ftdi_sio.c:1447: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1448: error: ‘struct ftdi_private’ has no member named ‘tx_bytes’
ftdi_sio.c:1449: warning: implicit declaration of function ‘spin_unlock_irqrestore’
ftdi_sio.c:1449: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1450: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:1451: error: ‘struct ftdi_private’ has no member named ‘rx_bytes’
ftdi_sio.c:1452: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:1454: error: dereferencing pointer to incomplete type
ftdi_sio.c:1455: error: dereferencing pointer to incomplete type
ftdi_sio.c:1462: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c:1469: error: dereferencing pointer to incomplete type
ftdi_sio.c:1470: error: dereferencing pointer to incomplete type
ftdi_sio.c:1470: warning: passing argument 1 of ‘ftdi_set_termios’ from incompatible pointer type
ftdi_sio.c:1475: error: ‘TIOCM_DTR’ undeclared (first use in this function)
ftdi_sio.c:1475: error: ‘TIOCM_RTS’ undeclared (first use in this function)
ftdi_sio.c:1475: warning: passing argument 1 of ‘update_mctrl’ from incompatible pointer type
ftdi_sio.c:1478: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:1479: error: ‘struct ftdi_private’ has no member named ‘rx_flags’
ftdi_sio.c:1480: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:1483: error: ‘struct ftdi_private’ has no member named ‘rx_processed’
ftdi_sio.c:1484: warning: implicit declaration of function ‘usb_fill_bulk_urb’
ftdi_sio.c:1484: error: dereferencing pointer to incomplete type
ftdi_sio.c:1485: warning: implicit declaration of function ‘usb_rcvbulkpipe’
ftdi_sio.c:1485: error: dereferencing pointer to incomplete type
ftdi_sio.c:1486: error: dereferencing pointer to incomplete type
ftdi_sio.c:1486: error: dereferencing pointer to incomplete type
ftdi_sio.c:1488: warning: implicit declaration of function ‘usb_submit_urb’
ftdi_sio.c:1488: error: dereferencing pointer to incomplete type
ftdi_sio.c:1488: error: ‘GFP_KERNEL’ undeclared (first use in this function)
ftdi_sio.c: At top level:
ftdi_sio.c:1506: warning: ‘struct file’ declared inside parameter list
ftdi_sio.c:1506: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:1506: error: conflicting types for ‘ftdi_close’
ftdi_sio.c:625: error: previous declaration of ‘ftdi_close’ was here
ftdi_sio.c: In function ‘ftdi_close’:
ftdi_sio.c:1508: error: dereferencing pointer to incomplete type
ftdi_sio.c:1509: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1514: error: ‘HUPCL’ undeclared (first use in this function)
ftdi_sio.c:1516: error: dereferencing pointer to incomplete type
ftdi_sio.c:1517: error: dereferencing pointer to incomplete type
ftdi_sio.c:1520: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c:1526: error: ‘TIOCM_DTR’ undeclared (first use in this function)
ftdi_sio.c:1526: error: ‘TIOCM_RTS’ undeclared (first use in this function)
ftdi_sio.c:1526: warning: passing argument 1 of ‘update_mctrl’ from incompatible pointer type
ftdi_sio.c:1530: warning: implicit declaration of function ‘cancel_delayed_work’
ftdi_sio.c:1530: error: ‘struct ftdi_private’ has no member named ‘rx_work’
ftdi_sio.c:1531: warning: implicit declaration of function ‘flush_scheduled_work’
ftdi_sio.c:1534: warning: implicit declaration of function ‘usb_kill_urb’
ftdi_sio.c:1534: error: dereferencing pointer to incomplete type
ftdi_sio.c: At top level:
ftdi_sio.c:1547: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:1546: error: conflicting types for ‘ftdi_write’
ftdi_sio.c:626: error: previous declaration of ‘ftdi_write’ was here
ftdi_sio.c: In function ‘ftdi_write’:
ftdi_sio.c:1549: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1557: error: dereferencing pointer to incomplete type
ftdi_sio.c:1563: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1564: error: ‘struct ftdi_private’ has no member named ‘tx_outstanding_urbs’
ftdi_sio.c:1565: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1569: error: ‘struct ftdi_private’ has no member named ‘tx_outstanding_urbs’
ftdi_sio.c:1570: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1580: error: ‘struct ftdi_private’ has no member named ‘max_packet_size’
ftdi_sio.c:1581: error: ‘struct ftdi_private’ has no member named ‘max_packet_size’
ftdi_sio.c:1584: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
ftdi_sio.c:1584: warning: assignment makes pointer from integer without a cast
ftdi_sio.c:1591: warning: implicit declaration of function ‘usb_alloc_urb’
ftdi_sio.c:1591: warning: assignment makes pointer from integer without a cast
ftdi_sio.c:1601: error: ‘struct ftdi_private’ has no member named ‘max_packet_size’
ftdi_sio.c:1613: warning: implicit declaration of function ‘memcpy’
ftdi_sio.c:1613: warning: incompatible implicit declaration of built-in function ‘memcpy’
ftdi_sio.c:1622: warning: incompatible implicit declaration of built-in function ‘memcpy’
ftdi_sio.c:1625: warning: implicit declaration of function ‘usb_serial_debug_data’
ftdi_sio.c:1625: error: dereferencing pointer to incomplete type
ftdi_sio.c:1628: error: dereferencing pointer to incomplete type
ftdi_sio.c:1629: warning: implicit declaration of function ‘usb_sndbulkpipe’
ftdi_sio.c:1629: error: dereferencing pointer to incomplete type
ftdi_sio.c:1629: error: dereferencing pointer to incomplete type
ftdi_sio.c:1639: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1640: error: ‘struct ftdi_private’ has no member named ‘tx_outstanding_bytes’
ftdi_sio.c:1641: error: ‘struct ftdi_private’ has no member named ‘tx_bytes’
ftdi_sio.c:1642: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1656: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1657: error: ‘struct ftdi_private’ has no member named ‘tx_outstanding_urbs’
ftdi_sio.c:1658: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c: At top level:
ftdi_sio.c:1665: warning: ‘struct urb’ declared inside parameter list
ftdi_sio.c:1665: error: conflicting types for ‘ftdi_write_bulk_callback’
ftdi_sio.c:629: error: previous declaration of ‘ftdi_write_bulk_callback’ was here
ftdi_sio.c: In function ‘ftdi_write_bulk_callback’:
ftdi_sio.c:1668: error: dereferencing pointer to incomplete type
ftdi_sio.c:1672: error: dereferencing pointer to incomplete type
ftdi_sio.c:1675: error: dereferencing pointer to incomplete type
ftdi_sio.c:1677: error: dereferencing pointer to incomplete type
ftdi_sio.c:1684: warning: assignment makes pointer from integer without a cast
ftdi_sio.c:1690: error: dereferencing pointer to incomplete type
ftdi_sio.c:1694: error: ‘struct ftdi_private’ has no member named ‘max_packet_size’
ftdi_sio.c:1694: error: ‘struct ftdi_private’ has no member named ‘max_packet_size’
ftdi_sio.c:1696: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1697: error: ‘struct ftdi_private’ has no member named ‘tx_outstanding_urbs’
ftdi_sio.c:1698: error: ‘struct ftdi_private’ has no member named ‘tx_outstanding_bytes’
ftdi_sio.c:1699: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1701: warning: implicit declaration of function ‘usb_serial_port_softint’
ftdi_sio.c: At top level:
ftdi_sio.c:1705: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:1705: error: conflicting types for ‘ftdi_write_room’
ftdi_sio.c:627: error: previous declaration of ‘ftdi_write_room’ was here
ftdi_sio.c: In function ‘ftdi_write_room’:
ftdi_sio.c:1707: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1711: error: dereferencing pointer to incomplete type
ftdi_sio.c:1713: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1714: error: ‘struct ftdi_private’ has no member named ‘tx_outstanding_urbs’
ftdi_sio.c:1724: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c: At top level:
ftdi_sio.c:1729: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:1729: error: conflicting types for ‘ftdi_chars_in_buffer’
ftdi_sio.c:628: error: previous declaration of ‘ftdi_chars_in_buffer’ was here
ftdi_sio.c: In function ‘ftdi_chars_in_buffer’:
ftdi_sio.c:1731: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1735: error: dereferencing pointer to incomplete type
ftdi_sio.c:1737: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c:1738: error: ‘struct ftdi_private’ has no member named ‘tx_outstanding_bytes’
ftdi_sio.c:1739: error: ‘struct ftdi_private’ has no member named ‘tx_lock’
ftdi_sio.c: At top level:
ftdi_sio.c:1749: warning: ‘struct urb’ declared inside parameter list
ftdi_sio.c:1749: error: conflicting types for ‘ftdi_read_bulk_callback’
ftdi_sio.c:630: error: previous declaration of ‘ftdi_read_bulk_callback’ was here
ftdi_sio.c: In function ‘ftdi_read_bulk_callback’:
ftdi_sio.c:1751: error: dereferencing pointer to incomplete type
ftdi_sio.c:1756: error: dereferencing pointer to incomplete type
ftdi_sio.c:1758: error: dereferencing pointer to incomplete type
ftdi_sio.c:1760: error: dereferencing pointer to incomplete type
ftdi_sio.c:1760: error: dereferencing pointer to incomplete type
ftdi_sio.c:1760: error: dereferencing pointer to incomplete type
ftdi_sio.c:1761: error: dereferencing pointer to incomplete type
ftdi_sio.c:1764: error: dereferencing pointer to incomplete type
ftdi_sio.c:1766: error: dereferencing pointer to incomplete type
ftdi_sio.c:1769: error: dereferencing pointer to incomplete type
ftdi_sio.c:1775: warning: assignment makes pointer from integer without a cast
ftdi_sio.c:1781: error: dereferencing pointer to incomplete type
ftdi_sio.c:1793: error: dereferencing pointer to incomplete type
ftdi_sio.c:1794: error: ‘struct ftdi_private’ has no member named ‘max_packet_size’
ftdi_sio.c:1794: error: ‘struct ftdi_private’ has no member named ‘max_packet_size’
ftdi_sio.c:1795: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:1796: error: ‘struct ftdi_private’ has no member named ‘rx_bytes’
ftdi_sio.c:1797: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:1799: error: ‘struct ftdi_private’ has no member named ‘rx_work’
ftdi_sio.c: At top level:
ftdi_sio.c:1804: warning: ‘struct work_struct’ declared inside parameter list
ftdi_sio.c:1804: error: conflicting types for ‘ftdi_process_read’
ftdi_sio.c:631: error: previous declaration of ‘ftdi_process_read’ was here
ftdi_sio.c: In function ‘ftdi_process_read’:
ftdi_sio.c:1807: warning: implicit declaration of function ‘container_of’
ftdi_sio.c:1807: error: expected expression before ‘struct’
ftdi_sio.c:1807: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:1808: error: ‘struct ftdi_private’ has no member named ‘port’
ftdi_sio.c:1820: error: dereferencing pointer to incomplete type
ftdi_sio.c:1822: error: dereferencing pointer to incomplete type
ftdi_sio.c:1825: error: dereferencing pointer to incomplete type
ftdi_sio.c:1831: warning: assignment makes pointer from integer without a cast
ftdi_sio.c:1837: error: dereferencing pointer to incomplete type
ftdi_sio.c:1843: error: dereferencing pointer to incomplete type
ftdi_sio.c:1845: error: ‘struct ftdi_private’ has no member named ‘rx_processed’
ftdi_sio.c:1847: error: ‘struct ftdi_private’ has no member named ‘rx_processed’
ftdi_sio.c:1848: error: dereferencing pointer to incomplete type
ftdi_sio.c:1848: error: ‘struct ftdi_private’ has no member named ‘rx_processed’
ftdi_sio.c:1851: error: dereferencing pointer to incomplete type
ftdi_sio.c:1852: error: dereferencing pointer to incomplete type
ftdi_sio.c:1852: error: dereferencing pointer to incomplete type
ftdi_sio.c:1865: error: ‘struct ftdi_private’ has no member named ‘rx_processed’
ftdi_sio.c:1865: error: dereferencing pointer to incomplete type
ftdi_sio.c:1865: error: ‘struct ftdi_private’ has no member named ‘max_packet_size’
ftdi_sio.c:1873: error: ‘struct ftdi_private’ has no member named ‘prev_status’
ftdi_sio.c:1874: error: ‘struct ftdi_private’ has no member named ‘diff_status’
ftdi_sio.c:1874: error: ‘struct ftdi_private’ has no member named ‘prev_status’
ftdi_sio.c:1875: warning: implicit declaration of function ‘wake_up_interruptible’
ftdi_sio.c:1875: error: ‘struct ftdi_private’ has no member named ‘delta_msr_wait’
ftdi_sio.c:1876: error: ‘struct ftdi_private’ has no member named ‘prev_status’
ftdi_sio.c:1880: warning: implicit declaration of function ‘min’
ftdi_sio.c:1880: error: ‘struct ftdi_private’ has no member named ‘max_packet_size’
ftdi_sio.c:1880: error: dereferencing pointer to incomplete type
ftdi_sio.c:1886: error: ‘struct ftdi_private’ has no member named ‘rx_flags’
ftdi_sio.c:1890: warning: implicit declaration of function ‘tty_buffer_request_room’
ftdi_sio.c:1897: error: ‘TTY_NORMAL’ undeclared (first use in this function)
ftdi_sio.c:1903: error: ‘TTY_OVERRUN’ undeclared (first use in this function)
ftdi_sio.c:1907: error: ‘TTY_BREAK’ undeclared (first use in this function)
ftdi_sio.c:1911: error: ‘TTY_PARITY’ undeclared (first use in this function)
ftdi_sio.c:1915: error: ‘TTY_FRAME’ undeclared (first use in this function)
ftdi_sio.c:1923: warning: implicit declaration of function ‘tty_insert_flip_char’
ftdi_sio.c:1953: warning: implicit declaration of function ‘tty_flip_buffer_push’
ftdi_sio.c:1956: error: dereferencing pointer to incomplete type
ftdi_sio.c:1958: error: ‘struct ftdi_private’ has no member named ‘rx_processed’
ftdi_sio.c:1961: error: dereferencing pointer to incomplete type
ftdi_sio.c:1963: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:1964: error: ‘struct ftdi_private’ has no member named ‘rx_flags’
ftdi_sio.c:1965: error: ‘struct ftdi_private’ has no member named ‘rx_flags’
ftdi_sio.c:1966: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:1971: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:1973: error: dereferencing pointer to incomplete type
ftdi_sio.c:1975: warning: implicit declaration of function ‘schedule_delayed_work’
ftdi_sio.c:1975: error: ‘struct ftdi_private’ has no member named ‘rx_work’
ftdi_sio.c:1983: error: ‘struct ftdi_private’ has no member named ‘rx_processed’
ftdi_sio.c:1986: error: dereferencing pointer to incomplete type
ftdi_sio.c:1988: error: dereferencing pointer to incomplete type
ftdi_sio.c:1988: error: dereferencing pointer to incomplete type
ftdi_sio.c:1989: error: dereferencing pointer to incomplete type
ftdi_sio.c:1989: error: dereferencing pointer to incomplete type
ftdi_sio.c:1990: error: dereferencing pointer to incomplete type
ftdi_sio.c:1990: error: dereferencing pointer to incomplete type
ftdi_sio.c:1993: error: dereferencing pointer to incomplete type
ftdi_sio.c:1993: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
ftdi_sio.c: At top level:
ftdi_sio.c:2002: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:2002: error: conflicting types for ‘ftdi_break_ctl’
ftdi_sio.c:636: error: previous declaration of ‘ftdi_break_ctl’ was here
ftdi_sio.c: In function ‘ftdi_break_ctl’:
ftdi_sio.c:2004: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:2019: error: dereferencing pointer to incomplete type
ftdi_sio.c:2019: error: dereferencing pointer to incomplete type
ftdi_sio.c:2022: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c: At top level:
ftdi_sio.c:2037: warning: ‘struct ktermios’ declared inside parameter list
ftdi_sio.c:2037: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:2037: error: conflicting types for ‘ftdi_set_termios’
ftdi_sio.c:632: error: previous declaration of ‘ftdi_set_termios’ was here
ftdi_sio.c: In function ‘ftdi_set_termios’:
ftdi_sio.c:2039: error: dereferencing pointer to incomplete type
ftdi_sio.c:2040: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:2041: error: dereferencing pointer to incomplete type
ftdi_sio.c:2042: error: dereferencing pointer to incomplete type
ftdi_sio.c:2047: error: dereferencing pointer to incomplete type
ftdi_sio.c:2054: error: ‘struct ftdi_private’ has no member named ‘force_baud’
ftdi_sio.c:2054: error: dereferencing pointer to incomplete type
ftdi_sio.c:2054: error: ‘CBAUD’ undeclared (first use in this function)
ftdi_sio.c:2054: error: ‘B0’ undeclared (first use in this function)
ftdi_sio.c:2056: error: dereferencing pointer to incomplete type
ftdi_sio.c:2056: error: ‘struct ftdi_private’ has no member named ‘force_baud’
ftdi_sio.c:2057: error: ‘struct ftdi_private’ has no member named ‘force_baud’
ftdi_sio.c:2061: error: ‘struct ftdi_private’ has no member named ‘force_rtscts’
ftdi_sio.c:2063: error: dereferencing pointer to incomplete type
ftdi_sio.c:2063: error: ‘CRTSCTS’ undeclared (first use in this function)
ftdi_sio.c:2066: error: dereferencing pointer to incomplete type
ftdi_sio.c:2077: error: dereferencing pointer to incomplete type
ftdi_sio.c:2077: error: ‘CMSPAR’ undeclared (first use in this function)
ftdi_sio.c:2080: error: ‘CSTOPB’ undeclared (first use in this function)
ftdi_sio.c:2082: error: ‘PARENB’ undeclared (first use in this function)
ftdi_sio.c:2083: error: ‘PARODD’ undeclared (first use in this function)
ftdi_sio.c:2086: error: ‘CSIZE’ undeclared (first use in this function)
ftdi_sio.c:2088: error: ‘CS5’ undeclared (first use in this function)
ftdi_sio.c:2089: error: ‘CS6’ undeclared (first use in this function)
ftdi_sio.c:2090: error: ‘CS7’ undeclared (first use in this function)
ftdi_sio.c:2091: error: ‘CS8’ undeclared (first use in this function)
ftdi_sio.c:2104: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c:2115: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c:2120: error: ‘TIOCM_DTR’ undeclared (first use in this function)
ftdi_sio.c:2120: error: ‘TIOCM_RTS’ undeclared (first use in this function)
ftdi_sio.c:2120: warning: passing argument 1 of ‘update_mctrl’ from incompatible pointer type
ftdi_sio.c:2123: warning: passing argument 1 of ‘change_speed’ from incompatible pointer type
ftdi_sio.c:2127: error: dereferencing pointer to incomplete type
ftdi_sio.c:2128: warning: passing argument 1 of ‘update_mctrl’ from incompatible pointer type
ftdi_sio.c:2140: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c:2152: error: ‘IXOFF’ undeclared (first use in this function)
ftdi_sio.c:2158: error: dereferencing pointer to incomplete type
ftdi_sio.c:2158: error: ‘VSTART’ undeclared (first use in this function)
ftdi_sio.c:2159: error: dereferencing pointer to incomplete type
ftdi_sio.c:2159: error: ‘VSTOP’ undeclared (first use in this function)
ftdi_sio.c:2167: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c:2179: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c: At top level:
ftdi_sio.c:2190: warning: ‘struct file’ declared inside parameter list
ftdi_sio.c:2190: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:2190: error: conflicting types for ‘ftdi_tiocmget’
ftdi_sio.c:633: error: previous declaration of ‘ftdi_tiocmget’ was here
ftdi_sio.c: In function ‘ftdi_tiocmget’:
ftdi_sio.c:2192: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:2200: error: dereferencing pointer to incomplete type
ftdi_sio.c:2201: warning: implicit declaration of function ‘usb_rcvctrlpipe’
ftdi_sio.c:2201: error: dereferencing pointer to incomplete type
ftdi_sio.c:2219: error: dereferencing pointer to incomplete type
ftdi_sio.c:2220: error: dereferencing pointer to incomplete type
ftdi_sio.c:2223: error: ‘struct ftdi_private’ has no member named ‘interface’
ftdi_sio.c:2235: error: ‘TIOCM_DSR’ undeclared (first use in this function)
ftdi_sio.c:2236: error: ‘TIOCM_CTS’ undeclared (first use in this function)
ftdi_sio.c:2237: error: ‘TIOCM_RI’ undeclared (first use in this function)
ftdi_sio.c:2238: error: ‘TIOCM_CD’ undeclared (first use in this function)
ftdi_sio.c: At top level:
ftdi_sio.c:2242: warning: ‘struct file’ declared inside parameter list
ftdi_sio.c:2242: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:2242: error: conflicting types for ‘ftdi_tiocmset’
ftdi_sio.c:634: error: previous declaration of ‘ftdi_tiocmset’ was here
ftdi_sio.c: In function ‘ftdi_tiocmset’:
ftdi_sio.c:2245: warning: passing argument 1 of ‘update_mctrl’ from incompatible pointer type
ftdi_sio.c: At top level:
ftdi_sio.c:2249: warning: ‘struct file’ declared inside parameter list
ftdi_sio.c:2249: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:2249: error: conflicting types for ‘ftdi_ioctl’
ftdi_sio.c:635: error: previous declaration of ‘ftdi_ioctl’ was here
ftdi_sio.c: In function ‘ftdi_ioctl’:
ftdi_sio.c:2251: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:2258: error: ‘TIOCGSERIAL’ undeclared (first use in this function)
ftdi_sio.c:2259: warning: implicit declaration of function ‘get_serial_info’
ftdi_sio.c:2259: error: expected ‘)’ before ‘__user’
ftdi_sio.c:2259: error: conversion to non-scalar type requested
ftdi_sio.c:2261: error: ‘TIOCSSERIAL’ undeclared (first use in this function)
ftdi_sio.c:2262: warning: implicit declaration of function ‘set_serial_info’
ftdi_sio.c:2262: error: expected ‘)’ before ‘__user’
ftdi_sio.c:2262: error: conversion to non-scalar type requested
ftdi_sio.c:2272: error: ‘TIOCMIWAIT’ undeclared (first use in this function)
ftdi_sio.c:2274: warning: implicit declaration of function ‘interruptible_sleep_on’
ftdi_sio.c:2274: error: ‘struct ftdi_private’ has no member named ‘delta_msr_wait’
ftdi_sio.c:2276: warning: implicit declaration of function ‘signal_pending’
ftdi_sio.c:2276: error: ‘current’ undeclared (first use in this function)
ftdi_sio.c:2277: error: ‘ERESTARTSYS’ undeclared (first use in this function)
ftdi_sio.c:2279: error: ‘struct ftdi_private’ has no member named ‘diff_status’
ftdi_sio.c:2286: error: ‘struct ftdi_private’ has no member named ‘diff_status’
ftdi_sio.c:2289: error: ‘TIOCM_RNG’ undeclared (first use in this function)
ftdi_sio.c:2290: error: ‘TIOCM_DSR’ undeclared (first use in this function)
ftdi_sio.c:2291: error: ‘TIOCM_CD’ undeclared (first use in this function)
ftdi_sio.c:2292: error: ‘TIOCM_CTS’ undeclared (first use in this function)
ftdi_sio.c:2314: error: ‘ENOIOCTLCMD’ undeclared (first use in this function)
ftdi_sio.c: At top level:
ftdi_sio.c:2318: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:2318: error: conflicting types for ‘ftdi_throttle’
ftdi_sio.c:637: error: previous declaration of ‘ftdi_throttle’ was here
ftdi_sio.c: In function ‘ftdi_throttle’:
ftdi_sio.c:2320: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:2323: error: dereferencing pointer to incomplete type
ftdi_sio.c:2325: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:2326: error: ‘struct ftdi_private’ has no member named ‘rx_flags’
ftdi_sio.c:2327: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c: At top level:
ftdi_sio.c:2331: warning: ‘struct usb_serial_port’ declared inside parameter list
ftdi_sio.c:2331: error: conflicting types for ‘ftdi_unthrottle’
ftdi_sio.c:638: error: previous declaration of ‘ftdi_unthrottle’ was here
ftdi_sio.c: In function ‘ftdi_unthrottle’:
ftdi_sio.c:2333: warning: initialization makes pointer from integer without a cast
ftdi_sio.c:2337: error: dereferencing pointer to incomplete type
ftdi_sio.c:2339: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:2340: error: ‘struct ftdi_private’ has no member named ‘rx_flags’
ftdi_sio.c:2341: error: ‘struct ftdi_private’ has no member named ‘rx_flags’
ftdi_sio.c:2342: error: ‘struct ftdi_private’ has no member named ‘rx_lock’
ftdi_sio.c:2345: error: ‘struct ftdi_private’ has no member named ‘rx_work’
ftdi_sio.c: At top level:
ftdi_sio.c:2348: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ftdi_init’
ftdi_sio.c:2378: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ftdi_exit’
ftdi_sio.c:2389: warning: data definition has no type or storage class
ftdi_sio.c:2389: warning: type defaults to ‘int’ in declaration of ‘module_init’
ftdi_sio.c:2389: warning: parameter names (without types) in function declaration
ftdi_sio.c:2390: warning: data definition has no type or storage class
ftdi_sio.c:2390: warning: type defaults to ‘int’ in declaration of ‘module_exit’
ftdi_sio.c:2390: warning: parameter names (without types) in function declaration
ftdi_sio.c:2392: error: expected declaration specifiers or ‘...’ before string constant
ftdi_sio.c:2392: warning: data definition has no type or storage class
ftdi_sio.c:2392: warning: type defaults to ‘int’ in declaration of ‘MODULE_AUTHOR’
ftdi_sio.c:2393: error: expected declaration specifiers or ‘...’ before string constant
ftdi_sio.c:2393: warning: data definition has no type or storage class
ftdi_sio.c:2393: warning: type defaults to ‘int’ in declaration of ‘MODULE_DESCRIPTION’
ftdi_sio.c:2394: error: expected declaration specifiers or ‘...’ before string constant
ftdi_sio.c:2394: warning: data definition has no type or storage class
ftdi_sio.c:2394: warning: type defaults to ‘int’ in declaration of ‘MODULE_LICENSE’
ftdi_sio.c:2396: error: expected ‘)’ before ‘|’ token
ftdi_sio.c:2397: error: expected ‘)’ before string constant
ftdi_sio.c:2398: error: expected ‘)’ before numeric constant
ftdi_sio.c:2399: error: expected ‘)’ before string constant
ftdi_sio.c:2401: error: expected ‘)’ before numeric constant
ftdi_sio.c:2402: error: expected ‘)’ before string constant
make: *** [ftdi_sio.o] Error 1

I dont what these means, and the .o file is not created finally. So I dont how to proceed. Please help me out to install the driver so that I can detect it with the USB port

---

### Post by mountain_goat on 2010-03-08
Are you wanting to use FTDI USB driver fro conection to an Arduino board?

---

