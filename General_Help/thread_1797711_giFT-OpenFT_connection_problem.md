---
title: "giFT-OpenFT connection problem"
date: 2011-07-05
forum: General Help
---

### Post by jillandjackk on 2011-07-05
Hello frnds,

Would anyone help me out in connecting the gift with OpenFT plugins.

When i run the giftd -v command at prompt.it displays the 

[18:57:02] giftd 0.11.8.1 (Aug  5 2008 14:35:39) started
[18:57:02] Plugin OpenFT (0.2.1.6) successfully loaded and initialized
[18:57:02] OpenFT: ft_openft.c:257(openft_start): Booya! OpenFT in the house!
[18:57:02] *** GIFT-WARNING: OpenFT: guessing max_active=600
[18:57:02] OpenFT: ft_node_cache.c:129(read_cache): opening nodes cache from /home/anil/.giFT/OpenFT/nodes...
[18:57:02] OpenFT: ft_node_cache.c:152(read_cache): successfully read 131 nodes
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.11.154.148:2145
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 24.11.154.148:2145: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 211.30.100.239:1215
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 211.30.100.239:1215: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 66.73.6.85:1926
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 66.73.6.85:1926: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 12.222.31.54:1215
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 12.222.31.54:1215: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 68.202.178.67:1215
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 68.202.178.67:1215: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 67.51.33.252:1215
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 67.51.33.252:1215: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.7.78.154:2145
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 24.7.78.154:2145: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 68.118.101.55:2145
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 68.118.101.55:2145: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 128.138.26.85:1523
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 128.138.26.85:1523: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 66.27.200.2:1935
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 66.27.200.2:1935: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.195.96.71:2145
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 24.195.96.71:2145: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.128.41.149:1215
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 24.128.41.149:1215: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 68.36.45.233:1215
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 68.36.45.233:1215: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 66.159.214.24:2131
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 66.159.214.24:2131: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.129.81.215:1215
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 24.129.81.215:1215: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 128.135.157.158:2191
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 128.135.157.158:2191: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 68.191.3.83:2145
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 68.191.3.83:2145: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 12.217.44.221:2145
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 12.217.44.221:2145: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 12.175.199.16:1215
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 12.175.199.16:1215: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 68.163.241.55:1215
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 68.163.241.55:1215: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 12.222.253.11:2145
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 12.222.253.11:2145: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 199.74.96.250:1215
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 199.74.96.250:1215: costs 4
[18:57:02] OpenFT: ft_session.c:637(ft_session_connect): attempting connection to 24.36.159.7:1215
[18:57:02] OpenFT: ft_conn.c:522(start_connection): 24.36.159.7:1215: costs 4
[18:57:02] OpenFT: ft_conn.c:642(ft_conn_initial): began 23 connections (remaining weight: 0)
[18:57:02] giFT: giftd.c:744(init_transfer): recovered 0 state transfers
[18:57:02] *** GIFT-WARNING: updating index...
[18:57:02] giFT: share_cache.c:855(share_write_index): entered
[18:57:02] giFT: share_cache.c:562(share_build_index): entered


And not able to connect through the front end like giFTcurs or apollon..

Thanks in advance.


I'm using ubuntu 10.4 version. Any suggestions are welcome...

---

