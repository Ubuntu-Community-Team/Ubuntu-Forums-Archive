---
title: "sar"
date: 2010-04-01
forum: General Help
---

### Post by Nick188 on 2010-04-01
Hi,

how can I use sar in order to get information about the scheduling?

regards

Nick.

---

### Post by Martje_001 on 2010-04-01
Install 'sysstat' with Synaptic and read the manual :):
```
SAR(1)                        Linux User's Manual                       SAR(1)



NAME
       sar - Collect, report, or save system activity information.

SYNOPSIS
       sar  [ -A ] [ -b ] [ -B ] [ -C ] [ -d ] [ -h ] [ -i interval ] [ -m ] [
       -p ] [ -q ] [ -r ] [ -R ] [ -S ] [ -t ] [ -u [ ALL ] ] [ -v ] [ -V ]  [
       -w  ] [ -W ] [ -y ] [ -n { keyword [,...] | ALL } ] [ -I { int [,...] |
       SUM | ALL | XALL } ] [ -P { cpu [,...] | ALL } ] [ -o [ filename ] | -f
       [  filename  ]  ]  [ -s [ hh:mm:ss ] ] [ -e [ hh:mm:ss ] ] [ interval [
       count ] ]

DESCRIPTION
       The sar command writes to standard  output  the  contents  of  selected
       cumulative  activity  counters  in the operating system. The accounting
       system, based on the values  in  the  count  and  interval  parameters,
       writes  information  the specified number of times spaced at the speciâ€
       fied intervals in seconds.  If the interval parameter is set  to  zero,
       the  sar command displays the average statistics for the time since the
       system was started. If the interval parameter is specified without  the
       count  parameter,  then  reports  are generated continuously.  The colâ€
       lected data can also be saved in the file specified by the -o  filename
       flag,  in  addition  to being displayed onto the screen. If filename is
       omitted, sar uses the standard system activity  daily  data  file,  the
       /var/log/sysstat/sadd  file,  where the dd parameter indicates the curâ€
       rent day.  By default all the data available from the kernel are  saved
       in the data file.

       The  sar  command extracts and writes to standard output records previâ€
       ously saved in a file. This file can be either the one specified by the
       -f flag or, by default, the standard system activity daily data file.

       Without  the -P flag, the sar command reports system-wide (global among
       all processors) statistics, which are calculated as averages for values
       expressed  as  percentages,  and  as  sums otherwise. If the -P flag is
       given, the sar command reports activity which relates to the  specified
       processor  or  processors.  If -P ALL is given, the sar command reports
       statistics for each individual processor and  global  statistics  among
       all processors.

       You  can  select  information  about  specific  system activities using
       flags. Not specifying any flags selects only CPU activity.   Specifying
       the  -A flag is equivalent to specifying -bBdqrRSvwWy -I SUM -I XALL -n
       ALL -u ALL -P ALL.

       The default version of the sar command (CPU utilization  report)  might
       be  one  of the first facilities the user runs to begin system activity
       investigation, because it monitors major system resources. If CPU  utiâ€
       lization  is near 100 percent (user + nice + system), the workload samâ€
       pled is CPU-bound.

       If multiple samples and multiple reports are desired, it is  convenient
       to  specify an output file for the sar command.  Run the sar command as
       a background process. The syntax for this is:

       sar -o datafile interval count >/dev/null 2>&1 &

       All data is captured in binary form and saved  to  a  file  (datafile).
       The  data  can then be selectively displayed with the sar command using
       the -f option. Set the interval and count parameters  to  select  count
       records  at  interval  second  intervals. If the count parameter is not
       set, all the records saved in the file will be selected.  Collection of
       data  in  this  manner  is  useful  to characterize system usage over a
       period of time and determine peak usage hours.

       Note:     The sar command only reports on local activities.


OPTIONS
       -A     This is equivalent to specifying -bBdqrRSuvwWy -I SUM -I XALL -n
              ALL -u ALL -P ALL.

       -b     Report  I/O  and transfer rate statistics.  The following values
              are displayed:

              tps
                     Total number of transfers per second that were issued  to
                     physical  devices.   A  transfer  is  an I/O request to a
                     physical device. Multiple logical requests  can  be  comâ€
                     bined  into a single I/O request to the device.  A transâ€
                     fer is of indeterminate size.

              rtps
                     Total number of read requests per second issued to physiâ€
                     cal devices.

              wtps
                     Total number of write requests per second issued to physâ€
                     ical devices.

              bread/s
                     Total amount of data read from the devices in blocks  per
                     second.   Blocks  are equivalent to sectors with 2.4 kerâ€
                     nels and newer and therefore have a size  of  512  bytes.
                     With older kernels, a block is of indeterminate size.

              bwrtn/s
                     Total  amount  of  data  written to devices in blocks per
                     second.

       -B     Report paging statistics. Some of the metrics below  are  availâ€
              able  only  with post 2.5 kernels. The following values are disâ€
              played:

              pgpgin/s
                     Total number of kilobytes the system paged in  from  disk
                     per second.  Note: With old kernels (2.2.x) this value is
                     a number of blocks per second (and not kilobytes).

              pgpgout/s
                     Total number of kilobytes the system paged  out  to  disk
                     per second.  Note: With old kernels (2.2.x) this value is
                     a number of blocks per second (and not kilobytes).

              fault/s
                     Number of page faults (major + minor) made by the  system
                     per second.  This is not a count of page faults that genâ€
                     erate I/O, because some page faults can be resolved withâ€
                     out I/O.

              majflt/s
                     Number  of  major  faults the system has made per second,
                     those which have required  loading  a  memory  page  from
                     disk.

              pgfree/s
                     Number of pages placed on the free list by the system per
                     second.

              pgscank/s
                     Number of pages scanned by the kswapd daemon per second.

              pgscand/s
                     Number of pages scanned directly per second.

              pgsteal/s
                     Number of pages  the  system  has  reclaimed  from  cache
                     (pagecache  and swapcache) per second to satisfy its memâ€
                     ory demands.

              %vmeff
                     Calculated as pgsteal / pgscan, this is a metric  of  the
                     efficiency  of  page  reclaim.  If  it  is near 100% then
                     almost every page coming off the  tail  of  the  inactive
                     list  is being reaped. If it gets too low (e.g. less than
                     30%) then the virtual memory is having  some  difficulty.
                     This  field  is  displayed  as zero if no pages have been
                     scanned during the interval of time.

       -C     When reading data from a file, tell sar to display comments that
              have been inserted by sadc.

       -d     Report  activity  for  each  block device (kernels 2.4 and newer
              only).  When data is displayed, the device specification dev m-n
              is  generally  used ( DEV column).  m is the major number of the
              device.  With recent kernels (post 2.5), n is the  minor  number
              of  the  device, but is only a sequence number with pre 2.5 kerâ€
              nels. Device names may also be pretty-printed if  option  -p  is
              used  (see  below). Values for fields avgqu-sz, await, svctm and
              %util may be unavailable and displayed as  0.00  with  some  2.4
              kernels.   Note  that  disk activity depends on sadc options "-S
              DISK" and "-S XDISK" to be collected. The following  values  are
              displayed:

              tps
                     Indicate  the  number  of  transfers per second that were
                     issued to the device.  Multiple logical requests  can  be
                     combined  into  a  single  I/O  request  to the device. A
                     transfer is of indeterminate size.

              rd_sec/s
                     Number of sectors read from the device.  The  size  of  a
                     sector is 512 bytes.

              wr_sec/s
                     Number  of  sectors  written to the device. The size of a
                     sector is 512 bytes.

              avgrq-sz
                     The average size (in sectors) of the requests  that  were
                     issued to the device.

              avgqu-sz
                     The average queue length of the requests that were issued
                     to the device.

              await
                     The average  time  (in  milliseconds)  for  I/O  requests
                     issued to the device to be served. This includes the time
                     spent by the requests in queue and the time spent servicâ€
                     ing them.

              svctm
                     The  average  service  time  (in  milliseconds)  for  I/O
                     requests that were issued to the device.

              %util
                     Percentage of CPU time during  which  I/O  requests  were
                     issued  to  the  device  (bandwidth  utilization  for the
                     device). Device saturation  occurs  when  this  value  is
                     close to 100%.

       -e [ hh:mm:ss ]
              Set  the  ending  time of the report. The default ending time is
              18:00:00. Hours must be given in 24-hour  format.   This  option
              can  be  used  when  data  are  read  from  or written to a file
              (options -f or -o ).

       -f [ filename ]
              Extract records from filename (created by the -o filename flag).
              The default value of the filename parameter is the current daily
              data file, the /var/log/sysstat/sadd  file.  The  -f  option  is
              exclusive of the -o option.

       -h     Display a short help message then exit.

       -i interval
              Select  data records at seconds as close as possible to the numâ€
              ber specified by the interval parameter.

       -I { int [,...] | SUM | ALL | XALL }
              Report statistics for a given interrupt.  int is  the  interrupt
              number.  Specifying  multiple  -I  int parameters on the command
              line will look at multiple independent interrupts.  The SUM keyâ€
              word  indicates that the total number of interrupts received per
              second is to be displayed. The ALL keyword indicates  that  staâ€
              tistics from the first 16 interrupts are to be reported, whereas
              the XALL keyword indicates that statistics from all  interrupts,
              including  potential APIC interrupt sources, are to be reported.
              Note that interrupt statistics depend on sadc option "-S INT" to
              be collected.

       -m     Report  power management statistics.  Note that these statistics
              depend on sadc option "-S POWER" to be collected.  The following
              value is displayed:

              MHz
                     CPU clock frequency in MHz.

       -n { keyword [,...] | ALL }
              Report network statistics.

              Possible keywords are DEV, EDEV, NFS, NFSD, SOCK, IP, EIP, ICMP,
              EICMP, TCP, ETCP, UDP, SOCK6, IP6, EIP6, ICMP6, EICMP6 and UDP6.

              With the DEV keyword, statistics from the  network  devices  are
              reported.  The following values are displayed:

              IFACE
                     Name  of  the  network interface for which statistics are
                     reported.

              rxpck/s
                     Total number of packets received per second.

              txpck/s
                     Total number of packets transmitted per second.

              rxkB/s
                     Total number of kilobytes received per second.

              txkB/s
                     Total number of kilobytes transmitted per second.

              rxcmp/s
                     Number of compressed packets  received  per  second  (for
                     cslip etc.).

              txcmp/s
                     Number of compressed packets transmitted per second.

              rxmcst/s
                     Number of multicast packets received per second.

              With  the EDEV keyword, statistics on failures (errors) from the
              network devices are reported.  The  following  values  are  disâ€
              played:

              IFACE
                     Name  of  the  network interface for which statistics are
                     reported.

              rxerr/s
                     Total number of bad packets received per second.

              txerr/s
                     Total number of errors that  happened  per  second  while
                     transmitting packets.

              coll/s
                     Number  of  collisions  that  happened  per  second while
                     transmitting packets.

              rxdrop/s
                     Number of received packets dropped per second because  of
                     a lack of space in linux buffers.

              txdrop/s
                     Number  of transmitted packets dropped per second because
                     of a lack of space in linux buffers.

              txcarr/s
                     Number of carrier-errors that happened per  second  while
                     transmitting packets.

              rxfram/s
                     Number of frame alignment errors that happened per second
                     on received packets.

              rxfifo/s
                     Number of FIFO overrun errors that happened per second on
                     received packets.

              txfifo/s
                     Number of FIFO overrun errors that happened per second on
                     transmitted packets.

              With the NFS keyword, statistics about NFS client  activity  are
              reported.  The following values are displayed:

              call/s
                     Number of RPC requests made per second.

              retrans/s
                     Number  of RPC requests per second, those which needed to
                     be retransmitted (for example because of a  server  timeâ€
                     out).

              read/s
                     Number of 'read' RPC calls made per second.

              write/s
                     Number of 'write' RPC calls made per second.

              access/s
                     Number of 'access' RPC calls made per second.

              getatt/s
                     Number of 'getattr' RPC calls made per second.

              With  the NFSD keyword, statistics about NFS server activity are
              reported.  The following values are displayed:

              scall/s
                     Number of RPC requests received per second.

              badcall/s
                     Number of bad RPC requests  received  per  second,  those
                     whose processing generated an error.

              packet/s
                     Number of network packets received per second.

              udp/s
                     Number of UDP packets received per second.

              tcp/s
                     Number of TCP packets received per second.

              hit/s
                     Number of reply cache hits per second.

              miss/s
                     Number of reply cache misses per second.

              sread/s
                     Number of 'read' RPC calls received per second.

              swrite/s
                     Number of 'write' RPC calls received per second.

              saccess/s
                     Number of 'access' RPC calls received per second.

              sgetatt/s
                     Number of 'getattr' RPC calls received per second.

              With the SOCK keyword, statistics on sockets in use are reported
              (IPv4).  The following values are displayed:

              totsck
                     Total number of sockets used by the system.

              tcpsck
                     Number of TCP sockets currently in use.

              udpsck
                     Number of UDP sockets currently in use.

              rawsck
                     Number of RAW sockets currently in use.

              ip-frag
                     Number of IP fragments currently in use.

              tcp-tw
                     Number of TCP sockets in TIME_WAIT state.

              With the IP keyword, statistics about IPv4 network  traffic  are
              reported.   Note  that IPv4 statistics depend on sadc option "-S
              SNMP" to be collected.  The following values are displayed (forâ€
              mal SNMP names between square brackets):

              irec/s
                     The  total number of input datagrams received from interâ€
                     faces per  second,  including  those  received  in  error
                     [ipInReceives].

              fwddgm/s
                     The  number of input datagrams per second, for which this
                     entity was not their final IP destination, as a result of
                     which an attempt was made to find a route to forward them
                     to that final destination [ipForwDatagrams].

              idel/s
                     The total number of input datagrams  successfully  delivâ€
                     ered  per  second  to  IP user-protocols (including ICMP)
                     [ipInDelivers].

              orq/s
                     The total number of IP datagrams which local IP user-proâ€
                     tocols  (including  ICMP)  supplied  per  second to IP in
                     requests for  transmission  [ipOutRequests].   Note  that
                     this  counter  does  not include any datagrams counted in
                     fwddgm/s.

              asmrq/s
                     The number of IP  fragments  received  per  second  which
                     needed to be reassembled at this entity [ipReasmReqds].

              asmok/s
                     The  number of IP datagrams successfully re-assembled per
                     second [ipReasmOKs].

              fragok/s
                     The number of IP datagrams that  have  been  successfully
                     fragmented at this entity per second [ipFragOKs].

              fragcrt/s
                     The number of IP datagram fragments that have been generâ€
                     ated per second as a  result  of  fragmentation  at  this
                     entity [ipFragCreates].

              With  the  EIP keyword, statistics about IPv4 network errors are
              reported.  Note that IPv4 statistics depend on sadc  option  "-S
              SNMP" to be collected.  The following values are displayed (forâ€
              mal SNMP names between square brackets):

              ihdrerr/s
                     The number of input datagrams discarded per second due to
                     errors in their IP headers, including bad checksums, verâ€
                     sion number mismatch, other format  errors,  time-to-live
                     exceeded,   errors  discovered  in  processing  their  IP
                     options, etc. [ipInHdrErrors]

              iadrerr/s
                     The  number  of  input  datagrams  discarded  per  second
                     because  the  IP address in their IP header's destination
                     field was not a valid address  to  be  received  at  this
                     entity.  This  count  includes  invalid  addresses (e.g.,
                     0.0.0.0) and  addresses  of  unsupported  Classes  (e.g.,
                     Class  E).  For  entities  which  are  not IP routers and
                     therefore do not forward datagrams, this counter includes
                     datagrams  discarded  because the destination address was
                     not a local address [ipInAddrErrors].

              iukwnpr/s
                     The number of locally-addressed datagrams  received  sucâ€
                     cessfully  but discarded per second because of an unknown
                     or unsupported protocol [ipInUnknownProtos].

              idisc/s
                     The number of input IP datagrams per second for which  no
                     problems were encountered to prevent their continued proâ€
                     cessing, but which were discarded (e.g., for lack of bufâ€
                     fer  space)  [ipInDiscards].  Note that this counter does
                     not  include  any  datagrams  discarded  while   awaiting
                     re-assembly.

              odisc/s
                     The number of output IP datagrams per second for which no
                     problem was encountered to prevent their transmission  to
                     their  destination,  but  which were discarded (e.g., for
                     lack of buffer space) [ipOutDiscards].   Note  that  this
                     counter  would  include  datagrams counted in fwddgm/s if
                     any such packets met this (discretionary) discard  criteâ€
                     rion.

              onort/s
                     The  number  of IP datagrams discarded per second because
                     no route could be found to transmit them to their  destiâ€
                     nation  [ipOutNoRoutes].  Note that this counter includes
                     any  packets  counted  in  fwddgm/s   which   meet   this
                     'no-route'  criterion.  Note that this includes any dataâ€
                     grams which a  host  cannot  route  because  all  of  its
                     default routers are down.

              asmf/s
                     The  number  of  failures  detected  per second by the IP
                     re-assembly algorithm (for whatever  reason:  timed  out,
                     errors,  etc) [ipReasmFails].  Note that this is not necâ€
                     essarily a count of discarded  IP  fragments  since  some
                     algorithms  can  lose track of the number of fragments by
                     combining them as they are received.

              fragf/s
                     The number of IP datagrams that have been  discarded  per
                     second  because  they  needed  to  be  fragmented at this
                     entity but could not be, e.g., because their Don't  Fragâ€
                     ment flag was set [ipFragFails].

              With  the  ICMP keyword, statistics about ICMPv4 network traffic
              are reported.  Note that ICMPv4 statistics depend on sadc option
              "-S  SNMP"  to be collected.  The following values are displayed
              (formal SNMP names between square brackets):

              imsg/s
                     The total  number  of  ICMP  messages  which  the  entity
                     received per second [icmpInMsgs].  Note that this counter
                     includes all those counted by ierr/s.

              omsg/s
                     The total number  of  ICMP  messages  which  this  entity
                     attempted  to  send  per second [icmpOutMsgs].  Note that
                     this counter includes all those counted by oerr/s.

              iech/s
                     The number of ICMP Echo (request) messages  received  per
                     second [icmpInEchos].

              iechr/s
                     The  number of ICMP Echo Reply messages received per secâ€
                     ond [icmpInEchoReps].

              oech/s
                     The number of ICMP Echo (request) messages sent per  secâ€
                     ond [icmpOutEchos].

              oechr/s
                     The  number  of  ICMP Echo Reply messages sent per second
                     [icmpOutEchoReps].

              itm/s
                     The number of ICMP Timestamp (request) messages  received
                     per second [icmpInTimestamps].

              itmr/s
                     The  number of ICMP Timestamp Reply messages received per
                     second [icmpInTimestampReps].

              otm/s
                     The number of ICMP Timestamp (request) messages sent  per
                     second [icmpOutTimestamps].

              otmr/s
                     The number of ICMP Timestamp Reply messages sent per secâ€
                     ond [icmpOutTimestampReps].

              iadrmk/s
                     The number of ICMP Address Mask Request messages received
                     per second [icmpInAddrMasks].

              iadrmkr/s
                     The  number  of ICMP Address Mask Reply messages received
                     per second [icmpInAddrMaskReps].

              oadrmk/s
                     The number of ICMP Address Mask Request messages sent per
                     second [icmpOutAddrMasks].

              oadrmkr/s
                     The  number  of ICMP Address Mask Reply messages sent per
                     second [icmpOutAddrMaskReps].

              With the EICMP keyword, statistics about ICMPv4  error  messages
              are reported.  Note that ICMPv4 statistics depend on sadc option
              "-S SNMP" to be collected.  The following values  are  displayed
              (formal SNMP names between square brackets):

              ierr/s
                     The  number  of ICMP messages per second which the entity
                     received but determined as  having  ICMP-specific  errors
                     (bad ICMP checksums, bad length, etc.) [icmpInErrors].

              oerr/s
                     The  number of ICMP messages per second which this entity
                     did not send due to problems discovered within ICMP  such
                     as a lack of buffers [icmpOutErrors].

              idstunr/s
                     The  number  of  ICMP  Destination  Unreachable  messages
                     received per second [icmpInDestUnreachs].

              odstunr/s
                     The number of ICMP Destination Unreachable messages  sent
                     per second [icmpOutDestUnreachs].

              itmex/s
                     The  number  of  ICMP Time Exceeded messages received per
                     second [icmpInTimeExcds].

              otmex/s
                     The number of ICMP Time Exceeded messages sent per second
                     [icmpOutTimeExcds].

              iparmpb/s
                     The  number  of  ICMP Parameter Problem messages received
                     per second [icmpInParmProbs].

              oparmpb/s
                     The number of ICMP Parameter Problem  messages  sent  per
                     second [icmpOutParmProbs].

              isrcq/s
                     The  number  of  ICMP Source Quench messages received per
                     second [icmpInSrcQuenchs].

              osrcq/s
                     The number of ICMP Source Quench messages sent per second
                     [icmpOutSrcQuenchs].

              iredir/s
                     The  number of ICMP Redirect messages received per second
                     [icmpInRedirects].

              oredir/s
                     The number of ICMP  Redirect  messages  sent  per  second
                     [icmpOutRedirects].

              With the TCP keyword, statistics about TCPv4 network traffic are
              reported.  Note that TCPv4 statistics depend on sadc option  "-S
              SNMP" to be collected.  The following values are displayed (forâ€
              mal SNMP names between square brackets):

              active/s
                     The number of times TCP connections have  made  a  direct
                     transition  to  the  SYN-SENT state from the CLOSED state
                     per second [tcpActiveOpens].

              passive/s
                     The number of times TCP connections have  made  a  direct
                     transition  to  the  SYN-RCVD state from the LISTEN state
                     per second [tcpPassiveOpens].

              iseg/s
                     The total number of segments received per second, includâ€
                     ing  those  received  in  error  [tcpInSegs].  This count
                     includes segments received on currently established  conâ€
                     nections.

              oseg/s
                     The  total  number of segments sent per second, including
                     those on current connections but excluding those containâ€
                     ing only retransmitted octets [tcpOutSegs].

              With the ETCP keyword, statistics about TCPv4 network errors are
              reported.  Note that TCPv4 statistics depend on sadc option  "-S
              SNMP" to be collected.  The following values are displayed (forâ€
              mal SNMP names between square brackets):

              atmptf/s
                     The number of times per second TCP connections have  made
                     a  direct  transition to the CLOSED state from either the
                     SYN-SENT state or the SYN-RCVD state, plus the number  of
                     times per second TCP connections have made a direct tranâ€
                     sition to  the  LISTEN  state  from  the  SYN-RCVD  state
                     [tcpAttemptFails].

              estres/s
                     The  number of times per second TCP connections have made
                     a direct transition to the CLOSED state from  either  the
                     ESTABLISHED  state  or  the CLOSE-WAIT state [tcpEstabReâ€
                     sets].

              retrans/s
                     The total number of segments retransmitted per  second  -
                     that  is, the number of TCP segments transmitted containâ€
                     ing one or more  previously  transmitted  octets  [tcpReâ€
                     transSegs].

              isegerr/s
                     The total number of segments received in error (e.g., bad
                     TCP checksums) per second [tcpInErrs].

              orsts/s
                     The number of TCP segments sent per second containing the
                     RST flag [tcpOutRsts].

              With the UDP keyword, statistics about UDPv4 network traffic are
              reported.  Note that UDPv4 statistics depend on sadc option  "-S
              SNMP" to be collected.  The following values are displayed (forâ€
              mal SNMP names between square brackets):

              idgm/s
                     The total number of UDP datagrams delivered per second to
                     UDP users [udpInDatagrams].

              odgm/s
                     The  total  number  of UDP datagrams sent per second from
                     this entity [udpOutDatagrams].

              noport/s
                     The total number of received UDP datagrams per second for
                     which  there  was  no application at the destination port
                     [udpNoPorts].

              idgmerr/s
                     The number of received  UDP  datagrams  per  second  that
                     could not be delivered for reasons other than the lack of
                     an application at the destination port [udpInErrors].

              With the  SOCK6  keyword,  statistics  on  sockets  in  use  are
              reported  (IPv6).   Note  that  IPv6  statistics  depend on sadc
              option "-S IPV6" to be collected.  The following values are disâ€
              played:

              tcp6sck
                     Number of TCPv6 sockets currently in use.

              udp6sck
                     Number of UDPv6 sockets currently in use.

              raw6sck
                     Number of RAWv6 sockets currently in use.

              ip6-frag
                     Number of IPv6 fragments currently in use.

              With  the IP6 keyword, statistics about IPv6 network traffic are
              reported.  Note that IPv6 statistics depend on sadc  option  "-S
              IPV6" to be collected.  The following values are displayed (forâ€
              mal SNMP names between square brackets):

              irec6/s
                     The total number of input datagrams received from  interâ€
                     faces  per  second,  including  those  received  in error
                     [ipv6IfStatsInReceives].

              fwddgm6/s
                     The number of output  datagrams  per  second  which  this
                     entity received and forwarded to their final destinations
                     [ipv6IfStatsOutForwDatagrams].

              idel6/s
                     The total number of datagrams successfully delivered  per
                     second  to IPv6 user-protocols (including ICMP) [ipv6IfSâ€
                     tatsInDelivers].

              orq6/s
                     The total number  of  IPv6  datagrams  which  local  IPv6
                     user-protocols  (including  ICMP)  supplied per second to
                     IPv6  in  requests  for  transmission  [ipv6IfStatsOutReâ€
                     quests].   Note  that  this  counter does not include any
                     datagrams counted in fwddgm6/s.

              asmrq6/s
                     The number of IPv6 fragments received  per  second  which
                     needed  to  be reassembled at this interface [ipv6IfStatâ€
                     sReasmReqds].

              asmok6/s
                     The number of IPv6 datagrams successfully reassembled per
                     second [ipv6IfStatsReasmOKs].

              imcpck6/s
                     The  number  of  multicast packets received per second by
                     the interface [ipv6IfStatsInMcastPkts].

              omcpck6/s
                     The number of multicast packets transmitted per second by
                     the interface [ipv6IfStatsOutMcastPkts].

              fragok6/s
                     The  number of IPv6 datagrams that have been successfully
                     fragmented at this output interface per second  [ipv6IfSâ€
                     tatsOutFragOKs].

              fragcr6/s
                     The  number  of  output datagram fragments that have been
                     generated per second as a result of fragmentation at this
                     output interface [ipv6IfStatsOutFragCreates].

              With  the EIP6 keyword, statistics about IPv6 network errors are
              reported.  Note that IPv6 statistics depend on sadc  option  "-S
              IPV6" to be collected.  The following values are displayed (forâ€
              mal SNMP names between square brackets):

              ihdrer6/s
                     The number of input datagrams discarded per second due to
                     errors  in  their  IPv6 headers, including version number
                     mismatch, other format errors, hop count exceeded, errors
                     discovered   in   processing  their  IPv6  options,  etc.
                     [ipv6IfStatsInHdrErrors]

              iadrer6/s
                     The  number  of  input  datagrams  discarded  per  second
                     because  the IPv6 address in their IPv6 header's destinaâ€
                     tion field was not a valid address to be received at this
                     entity. This count includes invalid addresses (e.g., ::0)
                     and unsupported addresses (e.g., addresses  with  unalloâ€
                     cated  prefixes). For entities which are not IPv6 routers
                     and therefore do  not  forward  datagrams,  this  counter
                     includes  datagrams  discarded  because  the  destination
                     address  was  not  a  local  address  [ipv6IfStatsInAddrâ€
                     Errors].

              iukwnp6/s
                     The  number  of locally-addressed datagrams received sucâ€
                     cessfully but discarded per second because of an  unknown
                     or unsupported protocol [ipv6IfStatsInUnknownProtos].

              i2big6/s
                     The number of input datagrams that could not be forwarded
                     per second because their size exceeded the  link  MTU  of
                     outgoing interface [ipv6IfStatsInTooBigErrors].

              idisc6/s
                     The  number  of input IPv6 datagrams per second for which
                     no problems were encountered to prevent  their  continued
                     processing,  but  which were discarded (e.g., for lack of
                     buffer space)  [ipv6IfStatsInDiscards].  Note  that  this
                     counter  does  not  include any datagrams discarded while
                     awaiting re-assembly.

              odisc6/s
                     The number of output IPv6 datagrams per second for  which
                     no  problem was encountered to prevent their transmission
                     to their destination, but which were discarded (e.g., for
                     lack of buffer space) [ipv6IfStatsOutDiscards]. Note that
                     this counter would include datagrams counted in fwddgm6/s
                     if any such packets met this (discretionary) discard criâ€
                     terion.

              inort6/s
                     The  number  of  input  datagrams  discarded  per  second
                     because no route could be found to transmit them to their
                     destination [ipv6IfStatsInNoRoutes].

              onort6/s
                     The number of locally generated  IP  datagrams  discarded
                     per  second  because  no route could be found to transmit
                     them to their destination [unknown formal SNMP name].

              asmf6/s
                     The number of failures detected per second  by  the  IPv6
                     re-assembly  algorithm  (for  whatever reason: timed out,
                     errors, etc.) [ipv6IfStatsReasmFails].  Note that this is
                     not necessarily a count of discarded IPv6 fragments since
                     some algorithms can lose track of the number of fragments
                     by combining them as they are received.

              fragf6/s
                     The number of IPv6 datagrams that have been discarded per
                     second because they needed to be fragmented at this  outâ€
                     put interface but could not be [ipv6IfStatsOutFragFails].

              itrpck6/s
                     The  number  of  input  datagrams  discarded  per  second
                     because datagram frame didn't carry enough data [ipv6IfSâ€
                     tatsInTruncatedPkts].

              With  the ICMP6 keyword, statistics about ICMPv6 network traffic
              are reported.  Note that ICMPv6 statistics depend on sadc option
              "-S  IPV6"  to be collected.  The following values are displayed
              (formal SNMP names between square brackets):

              imsg6/s
                     The total number of ICMP messages received by the  interâ€
                     face  per  second  which  includes  all  those counted by
                     ierr6/s [ipv6IfIcmpInMsgs].

              omsg6/s
                     The total number of ICMP messages  which  this  interface
                     attempted to send per second [ipv6IfIcmpOutMsgs].

              iech6/s
                     The  number  of  ICMP Echo (request) messages received by
                     the interface per second [ipv6IfIcmpInEchos].

              iechr6/s
                     The number of ICMP Echo Reply messages  received  by  the
                     interface per second [ipv6IfIcmpInEchoReplies].

              oechr6/s
                     The number of ICMP Echo Reply messages sent by the interâ€
                     face per second [ipv6IfIcmpOutEchoReplies].

              igmbq6/s
                     The number of  ICMPv6  Group  Membership  Query  messages
                     received  by the interface per second [ipv6IfIcmpInGroupâ€
                     MembQueries].

              igmbr6/s
                     The number of ICMPv6 Group Membership  Response  messages
                     received  by the interface per second [ipv6IfIcmpInGroupâ€
                     MembResponses].

              ogmbr6/s
                     The number of ICMPv6 Group Membership  Response  messages
                     sent per second [ipv6IfIcmpOutGroupMembResponses].

              igmbrd6/s
                     The  number of ICMPv6 Group Membership Reduction messages
                     received by the interface per second  [ipv6IfIcmpInGroupâ€
                     MembReductions].

              ogmbrd6/s
                     The  number of ICMPv6 Group Membership Reduction messages
                     sent per second [ipv6IfIcmpOutGroupMembReductions].

              irtsol6/s
                     The number of ICMP Router Solicit  messages  received  by
                     the interface per second [ipv6IfIcmpInRouterSolicits].

              ortsol6/s
                     The  number  of ICMP Router Solicitation messages sent by
                     the interface per second [ipv6IfIcmpOutRouterSolicits].

              irtad6/s
                     The number of ICMP Router Advertisement messages received
                     by the interface per second [ipv6IfIcmpInRouterAdvertiseâ€
                     ments].

              inbsol6/s
                     The number of ICMP Neighbor Solicit messages received  by
                     the interface per second [ipv6IfIcmpInNeighborSolicits].

              onbsol6/s
                     The number of ICMP Neighbor Solicitation messages sent by
                     the interface per second [ipv6IfIcmpOutNeighborSolicits].

              inbad6/s
                     The  number  of  ICMP  Neighbor  Advertisement   messages
                     received by the interface per second [ipv6IfIcmpInNeighbâ€
                     orAdvertisements].

              onbad6/s
                     The number of ICMP Neighbor Advertisement  messages  sent
                     by  the interface per second [ipv6IfIcmpOutNeighborAdverâ€
                     tisements].

              With the EICMP6 keyword, statistics about ICMPv6 error  messages
              are reported.  Note that ICMPv6 statistics depend on sadc option
              "-S IPV6" to be collected.  The following values  are  displayed
              (formal SNMP names between square brackets):

              ierr6/s
                     The  number  of ICMP messages per second which the interâ€
                     face received  but  determined  as  having  ICMP-specific
                     errors   (bad   ICMP   checksums,   bad   length,   etc.)
                     [ipv6IfIcmpInErrors]

              idtunr6/s
                     The  number  of  ICMP  Destination  Unreachable  messages
                     received by the interface per second [ipv6IfIcmpInDestUnâ€
                     reachs].

              odtunr6/s
                     The number of ICMP Destination Unreachable messages  sent
                     by the interface per second [ipv6IfIcmpOutDestUnreachs].

              itmex6/s
                     The number of ICMP Time Exceeded messages received by the
                     interface per second [ipv6IfIcmpInTimeExcds].

              otmex6/s
                     The number of ICMP Time Exceeded  messages  sent  by  the
                     interface per second [ipv6IfIcmpOutTimeExcds].

              iprmpb6/s
                     The number of ICMP Parameter Problem messages received by
                     the interface per second [ipv6IfIcmpInParmProblems].

              oprmpb6/s
                     The number of ICMP Parameter Problem messages sent by the
                     interface per second [ipv6IfIcmpOutParmProblems].

              iredir6/s
                     The number of Redirect messages received by the interface
                     per second [ipv6IfIcmpInRedirects].

              oredir6/s
                     The number of Redirect messages sent by the interface  by
                     second [ipv6IfIcmpOutRedirects].

              ipck2b6/s
                     The  number  of  ICMP Packet Too Big messages received by
                     the interface per second [ipv6IfIcmpInPktTooBigs].

              opck2b6/s
                     The number of ICMP Packet Too Big messages  sent  by  the
                     interface per second [ipv6IfIcmpOutPktTooBigs].

              With  the  UDP6  keyword, statistics about UDPv6 network traffic
              are reported.  Note that UDPv6 statistics depend on sadc  option
              "-S  IPV6"  to be collected.  The following values are displayed
              (formal SNMP names between square brackets):

              idgm6/s
                     The total number of UDP datagrams delivered per second to
                     UDP users [udpInDatagrams].

              odgm6/s
                     The  total  number  of UDP datagrams sent per second from
                     this entity [udpOutDatagrams].

              noport6/s
                     The total number of received UDP datagrams per second for
                     which  there  was  no application at the destination port
                     [udpNoPorts].

              idgmer6/s
                     The number of received  UDP  datagrams  per  second  that
                     could not be delivered for reasons other than the lack of
                     an application at the destination port [udpInErrors].

              The ALL keyword is equivalent to  specifying  all  the  keywords
              above and therefore all the network activities are reported.

       -o [ filename ]
              Save the readings in the file in binary form. Each reading is in
              a separate record. The default value of the  filename  parameter
              is  the current daily data file, the /var/log/sysstat/sadd file.
              The -o option is exclusive of  the  -f  option.   All  the  data
              available  from  the  kernel are saved in the file (in fact, sar
              calls its data collector sadc with  the  option  "-S  ALL".  See
              sadc(8) manual page).

       -P { cpu [,...] | ALL }
              Report  per-processor  statistics for the specified processor or
              processors.  Specifying the ALL keyword reports  statistics  for
              each  individual  processor,  and  globally  for all processors.
              Note that processor 0 is the first processor.

       -p     Pretty-print device names. Use this option in  conjunction  with
              option  -d.  By default names are printed as dev m-n where m and
              n are the major and minor numbers for the device.  Use  of  this
              option displays the names of the devices as they (should) appear
              in /dev.  Name  mappings  are  controlled  by  /etc/sysstat/sysâ€â€
              stat.ioconf.

       -q     Report  queue length and load averages. The following values are
              displayed:

              runq-sz
                     Run queue length (number of tasks waiting for run time).

              plist-sz
                     Number of tasks in the task list.

              ldavg-1
                     System load average for the last minute.  The load  averâ€
                     age  is  calculated  as the average number of runnable or
                     running tasks (R state), and the number of tasks in uninâ€
                     terruptible sleep (D state) over the specified interval.

              ldavg-5
                     System load average for the past 5 minutes.

              ldavg-15
                     System load average for the past 15 minutes.

       -r     Report  memory utilization statistics.  The following values are
              displayed:

              kbmemfree
                     Amount of free memory available in kilobytes.

              kbmemused
                     Amount of used memory in kilobytes. This  does  not  take
                     into account memory used by the kernel itself.

              %memused
                     Percentage of used memory.

              kbbuffers
                     Amount  of  memory used as buffers by the kernel in kiloâ€
                     bytes.

              kbcached
                     Amount of memory used to cache  data  by  the  kernel  in
                     kilobytes.

              kbcommit
                     Amount  of  memory  in kilobytes needed for current workâ€
                     load. This is an estimate of how much RAM/swap is  needed
                     to guarantee that there never is out of memory.

              %commit
                     Percentage of memory needed for current workload in relaâ€
                     tion to the total amount of memory (RAM+swap).  This numâ€
                     ber  may  be greater than 100% because the kernel usually
                     overcommits memory.


       -R     Report memory statistics. The following values are displayed:

              frmpg/s
                     Number of memory pages freed by the system per second.  A
                     negative  value represents a number of pages allocated by
                     the system.  Note that a page has a size of 4 kB or 8  kB
                     according to the machine architecture.

              bufpg/s
                     Number  of additional memory pages used as buffers by the
                     system per second.  A negative value  means  fewer  pages
                     used as buffers by the system.

              campg/s
                     Number  of  additional  memory pages cached by the system
                     per second.  A negative value means fewer  pages  in  the
                     cache.

       -s [ hh:mm:ss ]
              Set  the  starting  time of the data, causing the sar command to
              extract records time-tagged at, or following,  the  time  speciâ€
              fied.  The  default  starting  time  is 08:00:00.  Hours must be
              given in 24-hour format. This option can be used only when  data
              are read from a file (option -f ).

       -S     Report  swap space utilization statistics.  The following values
              are displayed:

              kbswpfree
                     Amount of free swap space in kilobytes.

              kbswpused
                     Amount of used swap space in kilobytes.

              %swpused
                     Percentage of used swap space.

              kbswpcad
                     Amount of cached swap memory in kilobytes.  This is  memâ€
                     ory  that  once  was  swapped out, is swapped back in but
                     still also is in the swap area (if memory  is  needed  it
                     doesn't  need  to  be  swapped  out  again  because it is
                     already in the swap area. This saves I/O).

              %swpcad
                     Percentage of cached  swap  memory  in  relation  to  the
                     amount of used swap space.

       -t     When  reading  data  from  a  daily data file, indicate that sar
              should display the timestamps in the original locale time of the
              data file creator. Without this option, the sar command displays
              the timestamps in the user's locale time.

       -u [ ALL ]
              Report CPU utilization. The ALL keyword indicates that  all  the
              CPU fields should be displayed.  The report may show the followâ€
              ing fields:

              %user
                     Percentage of CPU utilization that occurred while executâ€
                     ing at the user level (application). Note that this field
                     includes time spent running virtual processors.

              %usr
                     Percentage of CPU utilization that occurred while executâ€
                     ing at the user level (application). Note that this field
                     does NOT include time spent running virtual processors.

              %nice
                     Percentage of CPU utilization that occurred while executâ€
                     ing at the user level with nice priority.

              %system
                     Percentage of CPU utilization that occurred while executâ€
                     ing at the system level (kernel). Note  that  this  field
                     includes  time  spent  servicing  hardware  and  software
                     interrupts.

              %sys
                     Percentage of CPU utilization that occurred while executâ€
                     ing  at  the  system level (kernel). Note that this field
                     does NOT include time spent servicing hardware  or  softâ€
                     ware interrupts.

              %iowait
                     Percentage  of time that the CPU or CPUs were idle during
                     which the system had an outstanding disk I/O request.

              %steal
                     Percentage of time spent in involuntary wait by the  virâ€
                     tual  CPU  or  CPUs  while  the  hypervisor was servicing
                     another virtual processor.

              %irq
                     Percentage of time spent by the CPU or  CPUs  to  service
                     hardware interrupts.

              %soft
                     Percentage  of  time  spent by the CPU or CPUs to service
                     software interrupts.

              %guest
                     Percentage of time spent by the CPU or CPUs to run a virâ€
                     tual processor.

              %idle
                     Percentage of time that the CPU or CPUs were idle and the
                     system did not have an outstanding disk I/O request.

              Note: On SMP machines a processor that does not have any  activâ€
              ity  at  all (0.00 for every field) is a disabled (offline) proâ€
              cessor.

       -v     Report status of inode, file and other kernel tables.  The  folâ€
              lowing values are displayed:

              dentunusd
                     Number of unused cache entries in the directory cache.

              file-nr
                     Number of file handles used by the system.

              inode-nr
                     Number of inode handlers used by the system.

              pty-nr
                     Number of pseudo-terminals used by the system.

       -V     Print version number then exit.

       -w     Report task creation and system switching activity.

              proc/s
                     Total number of tasks created per second.

              cswch/s
                     Total number of context switches per second.

       -W     Report swapping statistics. The following values are displayed:

              pswpin/s
                     Total number of swap pages the system brought in per secâ€
                     ond.

              pswpout/s
                     Total number of swap pages the  system  brought  out  per
                     second.

       -y     Report TTY device activity. The following values are displayed:

              rcvin/s
                     Number  of  receive  interrupts  per  second  for current
                     serial line. Serial line number is given in the TTY  colâ€
                     umn.

              xmtin/s
                     Number  of  transmit  interrupts  per  second for current
                     serial line.

              framerr/s
                     Number of frame errors  per  second  for  current  serial
                     line.

              prtyerr/s
                     Number  of  parity  errors  per second for current serial
                     line.

              brk/s
                     Number of breaks per second for current serial line.

              ovrun/s
                     Number of overrun errors per second  for  current  serial
                     line.

              Note  that  with  recent  2.6  kernels,  these statistics can be
              retrieved only by root.


ENVIRONMENT
       The sar command takes into account the following environment variables:


       S_TIME_FORMAT
              If this variable exists and its value is ISO  then  the  current
              locale  will  be  ignored  when  printing the date in the report
              header.   The  sar  command  will  use  the  ISO   8601   format
              (YYYY-MM-DD) instead.


       S_TIME_DEF_TIME
              If  this variable exists and its value is UTC then sar will save
              its data in UTC time (data will  still  be  displayed  in  local
              time).   sar  will  also  use  UTC time instead of local time to
              determine  the  current  daily  data   file   located   in   the
              /var/log/sysstat  directory.  This  variable  may  be useful for
              servers with users located across several timezones.

EXAMPLES
       sar -u 2 5
              Report CPU utilization for each 2  seconds.  5  lines  are  disâ€
              played.

       sar -I 14 -o int14.file 2 10
              Report  statistics  on  IRQ  14 for each 2 seconds. 10 lines are
              displayed.  Data are stored in a file called int14.file.

       sar -r -n DEV -f /var/log/sysstat/sa16
              Display memory and network statistics saved in daily  data  file
              'sa16'.

       sar -A
              Display all the statistics saved in current daily data file.

BUGS
       /proc filesystem must be mounted for the sar command to work.

       All the statistics are not necessarily available, depending on the kerâ€
       nel version used.

FILES
       /var/log/sysstat/sadd
              Indicate the daily data file, where the dd parameter is a number
              representing the day of the month.

       /proc contains various files with system statistics.

AUTHOR
       Sebastien Godard (sysstat <at> orange.fr)

SEE ALSO
       sadc(8),  sa1(8),  sa2(8),  sadf(1),  isag(1),  pidstat(1),  mpstat(1),
       iostat(1), vmstat(8)

       http://pagesperso-orange.fr/sebastien.godard/



Linux                              MAY 2009                             SAR(1)
```

---

### Post by kjohri on 2012-07-21
Try 
```
sar -q
```
for run queue length and load averages.

The following link gives an example,

[http://www.softprayog.in/tutorials/sar-command-for-system-activity-reports]("http://www.softprayog.in/tutorials/sar-command-for-system-activity-reports")

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

