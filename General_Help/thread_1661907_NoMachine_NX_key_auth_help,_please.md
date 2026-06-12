---
title: "NoMachine NX key auth help, please"
date: 2011-01-07
forum: General Help
---

### Post by MrDetermination on 2011-01-07
I did get [FreeNX working]("http://ohioloco.ubuntuforums.org/showthread.php?t=1658387") only to find out that it has [issues resuming sessions]("https://bugs.launchpad.net/freenx-server/+bug/589723") which is a critical bit of functionality for my situation.

sudo apt-get remove freenx

Installed the latest nomachine packages on Lucid.  
Ran the install script.  
Added a user.  
Generated new keys.
Changes permissions
connect fine with ssh
can't get anywhere with NX :(

```
FRED@blackbox:~$ sudo /usr/NX/bin/nxserver --usercheck FRED
[sudo] password for FRED:
NX> 900 Verifying public key authentication for NX user: FRED.
NX> 900 Adding public key for user: FRED to the authorized keys file.
NX> 900 Verifying public key authentication for NX user: FRED.
NX> 500 ERROR: Public key authentication failed
NX> 500 WARNING: NX server was unable to login as user: FRED
NX> 500 WARNING: Please check that the account is enabled to login.
NX> 500 WARNING: Also check that user's home directory, the directory
NX> 500 WARNING: ~/.ssh and the file ~/.ssh/authorized_keys2 have
NX> 500 WARNING: correct permissions according to the StrictModes of
NX> 500 WARNING: your SSHD configuration
NX> 999 Bye.

```

copied key out to Windows

from the windows client:
```
NX> 203 NXSSH running with pid: 3028
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.0.11 on port: 2022
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.4.0-14 - LFE
NX> 105 Hello NXCLIENT - Version 3.4.0
NX> 134 Accepted protocol: 3.4.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: FRED
NX> 102 Password: ********
NX> 103 Welcome to: blackbox user: FRED
NX> 105 Listsession --user="FRED" --status="suspended\054running" --geometry="1920x1200x32+render" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: FRED
NX> 105 Start session with: --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="blackbox.local" --type="unix-gnome" --geometry="1024x768" --client="winnt" --keyboard="pc102\057en_US" --screeninfo="1024x768x32+render" 
NX> 502 ERROR: Public key authentication failed
NX> 502 ERROR: NX server was unable to login as user: FRED
NX> 502 ERROR: Please check that the account is enabled to login,
NX> 502 ERROR: the user's home directory, the directory ~/.ssh
NX> 502 ERROR: and the file ~/.ssh/authorized_keys2 have correct
NX> 502 ERROR: permissions setting according to the StrictModes
NX> 502 ERROR: of your SSHD configuration.
NX> 999 Bye.
NX> 280 Exiting on signal: 15
```

node.cfg
```
#
# Set config file format version.
#
ConfigFileVersion = "2.0"

#
# Set the log level of NX node. NX node logs to the syslog all the
# events that are <= to the level specified below, according to the
# following convention:
#
# KERN_ERR         3: Error condition.
# KERN_INFO        6: Informational.
# KERN_DEBUG       7: Debug messages.
#
# Note, anyway, that NX node uses level 6 in the syslog to log the 
# event. This is intended to override any setting on the local sys-
# log configuration that would prevent the event from being actually
# logged.
#
# The suggested values are:
#
# 6: This is the default value. Only the important events
#    are logged.
#
# 7: Set the log level to debug.
#
#SessionLogLevel = "6"

#
# Specify hostname for the NX node. 
#
#NodeName = "localhost.localdomain"

#
# Enable or disable the automatic clean-up of NX session directories
# at the time sessions are terminated:
#
# 1: Enabled. This is the default value.
#
# 0: Disabled. Directories are prefixed by 'T-' and left
#    for further reference.
#
#SessionLogClean = "1"

#
# Enable or disable NX node to log the X client stderr.
#
# 1: Enabled. The standard error of the X clients is redirected to
#    the 'clients' file in the session directory. 
#
# 0: Disabled. The standard error of the X clients is redirected to
#    /dev/null.
#
#ClientLog = "1"

#
# Set the maximum size allowed for the log of the X clients. The node
# will terminate the session if this limit is exceeded. The default 
# value is 4194304 bytes (4MB).
#
#ClientLogLimit = "4194304"

#
# Set the maximum size allowed for the session log. The node will
# terminate the session if this limit is exceeded. The default value
# is 4194304 bytes (4MB).
#
#SessionLogLimit = "4194304"

#
# Set the maximum amount of data that can be copied from within the 
# NX session to the client. The default value is unlimited. Limit for 
# the size of the buffer on copy operations has to be specified in 
# bytes. 
#
#ClipboardBufferLimit = "unlimited"

#
# Enable or disable SSL encryption of all traffic between server and
# node.
#
# 1: Enabled. Unencrypted connections between the server and
#    the node will be allowed.                       
#
# 0: Disabled. Forbid the use of unencrypted connections. The
#    node will force the server to tunnel the proxy connections
#    over the encrypted channel.
#
# Session negotiation always happens across an encrypted channel.
# Normally the user can specify if the subsequent communication
# must take place through a direct connection between the proxies
# or by tunneling it through SSH. You may uncomment the following
# line and set the value to 0 to increase the security of the node
# host or if NX node is behind a firewall preventing the access to
# the set of ports used by the NX node.
#
# Unencrypted sessions require that the firewall lets the proxies
# communicate over the TCP ports ranging from:
#
# DISPLAY_BASE + 4000
#
# to:
#
# DISPLAY_BASE + 4000 + DISPLAY_LIMIT
#
# By default the user is allowed to specify if a session will run
# unencrypted, for example when running the session across the same
# LAN or when performance is an issue.
#
EnableUnencryptedSession = "0"

#
# Specify path and name of the client to be run by nxnode, nxcomp
# and nxagent, for example for issuing dialog boxes and messages,
# instead of the default nxclient.
#
#CommandClient = "/usr/NX/bin/nxclient"

#
# Specify path and name of the command 'fuser' to identify processes
# using files or sockets.
#
CommandFuser = "/bin/fuser"

#
# Specify path and name of the command 'lsof' to list open files.
#
#CommandLsof = "/usr/sbin/lsof"

#
# Specify path and name of the command 'xauth' to edit and display
# the authorization information used when connecting to the X server.
#
#CommandXauth = "xauth"

#
# Specify path and name of the command 'xdpyinfo' for displaying
# information about an X server.
#
#CommandXdpyInfo = "xdpyinfo"

#
# Specify path and name of the command 'xmodmap' to edit and display
# the keyboard modifier map and keymap table.
#
#CommandXmodmap = "xmodmap"

#
# Specify path and name of the command starting 'CDE'.
#
#CommandStartCDE = "cdwm"

#
# Specify path and name of the command to start the RDP Client.
#
#CommandStartRDP = "rdesktop -f"

#
# Specify path and name of the command to start the RFB Client.
#
#CommandStartRFB = "vncviewer -fullscreen"

#
# Enable or disable use of 'xkbcomp' command:
#
# 1: Enabled. Use 'xkbcomp' command.
#
# 0: Disabled.
#
#EnableCommandXkbComp = "1"

#
# Specify path and name of the command 'xkbcomp' to compile XKB key-
# board description.
#
#CommandXkbComp = "xkbcomp"

#
# Specify location and file name of the keymap file used by 'xkbcomp'.
#
#XkbCompKeymapFile = "/etc/X11/xkb/keymap/xfree86"

#
# Specify the location and file name of the SSH authorized keys.
#
SSHAuthorizedKeys = "authorized_keys2"

#
# Specify the font server to be used by NX agent. By default the NX
# agent only uses the X11 system fonts. Uncomment the following line
# to enable use of an X Font Server.
#
#AgentFontServer = "unix/:7100"

#
# Specify the path of default X window system startup script.
#
#DefaultXSession = "/etc/X11/xdm/Xsession"

#
# Set the default DPI of the X server to the specified value. This
# should normally not be required, but some desktop applications fail
# to set an appropriate value and fall back to 75 DPI, which is the
# value reported by default by the X server.
#
#DefaultXDPI = "96"

#
# Specify the path of libraries to be added to the agents environment.
# Be sure that NX libraries are listed first.
#
#AgentLibraryPath = "/usr/NX/lib"

#
# Specify the path of libraries to be added to NX proxy environment.
#
#ProxyLibraryPath = "/usr/NX/lib"

#
# Specify a list of libraries to be preloaded in X applications. This key
# is only used when running sessions in single application mode without NX 
# agent encoding. Starting from version 1.5.0, the node doesn't preload the
# NX X11 libraries.
#
# The default is an empty list.
#
# ApplicationLibraryPreload = "/usr/NX/lib/libX11.so.6.2:/usr/NX/lib/libXext.so.6.4:/usr/NX/lib/libXcomp.so.1:/usr/NX/lib/libXcompext.so.1:/usr/NX/lib/libXrender.so.1.2"
#
#ApplicationLibraryPreload = ""

#
# Specify a list of directories to be added to the library path of X
# clients when run inside a session in single application mode without
# NX agent encoding.
#
# The default is an empty list.
#
# ApplicationLibraryPath = "/usr/NX/lib" 
#
#ApplicationLibraryPath = ""

#
# Enable or disable TCP_NODELAY setting in NX proxy.
#
# 1: Enabled. Let NX client choose whether to enable or not TCP_NODELAY
#    on proxy socket.
#
# 0: Disabled. Disable TCP_NODELAY.
#
# Due to a bug in old Linux kernels, enabling TCP_NODELAY when running
# sessions over PPP links can cause sessions to fail if a serious net-
# work congestion is encountered.
#
#ProxyTCPNodelay = "0"

#
# Specify a list of comma-separated options to be added to the
# NX proxy transport. Look at the NX proxy documentation for more
# information about the available options. Options specified in 
# 'ProxyExtraOptions' override the parameters set by NX client.
#
#ProxyExtraOptions = "limit=256k,link=modem"

#
# Append arguments to the command line used to run the NX agent for
# X (Unix sessions).
#
# Mutiple parameters can be specified by separating them with a blank
# character. Note that, for security reasons, no shell interpretation
# is made.
#
#AgentExtraOptions = "-nocomposite -noshpix"

#
# Specify the default Window Manager to be used when running single
# applications in a virtual desktop.
#
#DefaultXWM = "twm"

#
# Specify the domain of the Windows Terminal Server.
#
#DefaultRDPDomain = ""

#
# Specify the path of base directory where the NX node has to mount
# shares exported by the user. The default value is $(HOME)/MyShares.
#
#ShareBasePath = "$(HOME)/MyShares"

#
# Allow the node to use privileged scripts to manage the shares:
# 
# 1: Enabled. The node will use the suid scripts to mount and 
#    unmount the client shares using the SMB or CIFS file-
#    sharing protocol depending on which protocol is available
#    on both client and server side.
#
# 0: Disabled. The node will forbid any attempt to mount the
#    client shares.
#
#EnableFileSharing = "1"

#
# Specify the path of the directory holding CUPS binaries (f.e. the
# 'lpoptions' program).
#
CUPSBinPath = "/usr/bin"

#
# Specify the path of the directory holding CUPS programs and reserved
# for administrative purposes (f.e. 'cupsd' or 'lpadmin').
#
CUPSSbinPath = "/usr/sbin"

#
# Enable or disable CUPS support:
#
# 1: Enabled. Enable CUPS support.
#
# 0: Disabled. Disable CUPS support.
#
EnableCUPSSupport = "1"

#
# Specify the file-sharing protocol to be used for attaching the
# filesystem to the target directory set by the ShareBasePath
# key. The possible values are both, smbfs, cifs or none. 
#
MountShareProtocol = "smbfs"

#
# Specify the TCP port where the NX node SSHD daemon is running.
#
SSHDPort = "2022"

#
# Accept or refuse the NX client connection if SSHD does not export
# the 'SSH_CONNECTION' and 'SSH_CLIENT' variables in the environment
# passed to the NX node.
#
# 1: Refuse. Check the remote IP and don't accept the connection if it
#    can't be determined.
#
# 0: Accept. Check the remote IP and accept the connection even if the
#    remote IP is not provided.
#
#SSHDCheckIP = "0"

#
# Enable or disable running nxsensor:
#
# 1: Enabled.
#
# 0: Disabled.
# 
# Run the nxsensor daemon in the background. This daemon can be used
# to produce statistics about the node machine. Produced data is to
# be queried and elaborated by the nxstat daemon running on the NX
# server host machine.
#
#EnableSensor = "0"

#
# Specify the hostname or IP address where the nxstat daemon, in
# charge of collecting and elaborating data provided by nxsensor,
# will be assumed to run.
#
#StatisticsHost = "127.0.0.1"

#
# The port where the NX server will contact the nxsensor daemon to
# collect the statistics data. The key is also used by nxsensor to
# find out the network interface where it will listen for incoming
# connections.
#
#NodeSensorPort = "19250"

#
# If set, the specified message will be provided to the user if this 
# is the first time the user starts a session on this node. 
#
#NodeFirstLoginGreeting = "Welcome to your NX session"

#
# If set, the specified message will be provided to the user every
# time he/she has started a new session on this node.
#
NodeLoginGreeting = "New session"

#
# Specify a different path from the default, i.e. user's home, where
# the .nx directory has to be created to store session files. If it
# doesn't exist yet, NX node will try to create a sub-directory for
# each of the users starting a session there, named as username, and
# will create the .nx under that sub-directory. For example, if this
# key is set to /tmp/nxdir/, when user nxtest runs the first session,
# the node will try to create the /tmp/nxdir/nxtest/.nx directory.
# The directory specifed in the UserNXDirectoryPath key needs to
# have proper ownership and permissions set to ensure that the node,
# running as the user, can access it. I.e. the directory should be
# writeable for all users or alternatively, the administrator should
# create a directory, with proper ownership and permissions, named as
# username, for each of the users who need to start sessions there.
#
#UserNXDirectoryPath = ""

#
# Specify absolute path of the custom script to be executed before
# the session start-up. The script can accept session ID, username
# and session type as its input.
#
# E.g. UserScriptBeforeSessionStart = "/tmp/nxscript/script.sh"
#
#UserScriptBeforeSessionStart = ""

#
# Specify absolute path of the custom script to be executed after the
# session start-up. The script can accept session ID, username and
# session type as its input.
#
#UserScriptAfterSessionStart = ""

#
# Specify absolute path of the custom script to be executed before
# the session is suspended. The script can accept session ID and
# username as its input.
#
#UserScriptBeforeSessionSuspend = ""

#
# Specify absolute path of the custom script to be executed after the
# session is suspended. The script can accept session ID and username
# as its input.
#
#UserScriptAfterSessionSuspend = ""

#
# Specify absolute path of the custom script to be executed before the
# session is closed. The script can accept session ID and username as
# its input.
#
#UserScriptBeforeSessionClose = ""

#
# Specify absolute path of the custom script to be executed after the
# session is closed. The script can accept session ID and username as
# its input.
#
#UserScriptAfterSessionClose = ""

#
# Specify absolute path of the custom script to be executed before
# the session is reconnected. The script can accept session ID and
# username as its input.
#
#UserScriptBeforeSessionReconnect = ""

#
# Specify absolute path of the custom script to be executed after the
# session is reconnected. The script can accept session ID and user-
# name as its input.
#
#UserScriptAfterSessionReconnect = ""

#
# Specify absolute path of the custom script to be executed after
# session failure. The script can accept session ID, username and
# session type as its input.
#
#UserScriptAfterSessionFailure = ""

#
# Enable or disable the pulldown dialog, which provides a graphical
# way to suspend or terminate the rootless session:
#
# 1: Enabled. The pulldown menu is shown when the mouse pointer
#    moves near the middle of the top boundary of a window and
#    allows the user to suspend or terminate the session by means
#    of an icon-click.
#
# 0: Disabled. The ctrl+alt+T key combination has to be issued
#    to get the dialog for suspending or terminating the session.
#
#EnablePulldownMenu = "1"

#
# Set for how long NX node has to wait for a reply from NX Server
# before considering that the connection with the server has been 
# lost. The default value, 120, lets NX node wait for 2 minutes.
# Set this value to 0 to disable timeout on the node.
#
#NodeConnectionTimeout = "120"

#
# Specify path and name of the command to start the GNOME session.
#
CommandStartGnome = "/etc/gdm/Xsession gnome-session"

#
# Specify path and name of the command to start the KDE session.
#
CommandStartKDE = "/etc/X11/Xsession startkde"

#
# Allow the server to use the privileged scripts to manage the SMB
#  shares.
# 
#  1: Enabled. When running the commands as the target user doesn't
#     work, the server will use the suid scripts to mount and unmount
#     the client shares.
# 
#  0: Disabled. Using the privileged scripts will not be allowed.
#     The mount will only be attempted by running the command as the
#     target user. If the host server is configured to forbid mounts by
#     unprivileged users, the operation will fail.
# 
#  By default, NX node will not use the privileged scripts so that the
#  system will behave according to the suid settings of the smbmount
#  and smbumount commands.
# 
#  Normally smbmount and smbumount can be set suid root to allow any
#  unprivileged user to mount his/her resources. By clearing the suid
#  bit and by letting the node use the privileged scripts, the system
#  administrator can gain greater control on the host node, by allowing
#  unprivileged users to mount their shares only within a NX session.  
#
#EnablePrivilegedSmbScripts = "0"

#
# Specify if NX node has to add shared printers to CUPS by using the 
# IP address of the node or localhost. Specifying 'ip' is needed for
# CUPS versions minor than 1.2, otherwise 'localhost' can be used.
#
CUPSAddPrinterMode  = "localhost"
```

server.cfg
```
EnableNodeMonitoring = "1"
SSHDPort = "2022"
EnableUnencryptedSession = "0"
SSHDAuthPort = "2022"
EnableStatistics = "1"
EnablePasswordDB = "1"
#
# Allow the root user to run NX sessions.
#
# 1: Enabled. Allow an NX user to run sessions as user with
#    administrative rights.
#
# 0: Disabled. NX server forbids a NX user to log as user
#    having administrative privileges.
#
#EnableAdministratorLogin = "0"

#
# Set the User Identifier (UID) number for NX users. If an empty value
# is specified, the NX server will create the account with the default 
# value set on the system.
#
#UserId = "10"

#
# Set the Group Identifier (GID) for NX users. If an empty value is
# specified, the NX server will create the account with the default
# value set on the system.
#
#UserGroup = "users"

#
# Set the home directory for NX users. If an empty value is specified,
# the NX server will create the user's home in the default directory
# set on the system.
#
#UserHome = "/home"

#
# Specify the port where the server will contact the nxsensor daemons
# to collect the statistics.
#
#ServerSensorPort = "19250"

#
# Set for how long the NX server daemon has to wait for a reply from
# the node machine before considering that this host is unreachable.
# The default value, 10, let NX server daemon to wait for 10 seconds.
#
#NodeResponseTimeout = "10"

#
# Enable or disable support for user profiles:
#
# 1: Enabled. The NX server allows the NX session to start
#    according to the set of rules specified for the system
#    or on a per-user basis.
#
# 0: Disabled. The NX server starts the session without apply-
#    ing any rules.
#
# The administrator can configure access to applications and nodes
# by creating a specific profile for the NX system, which will be
# applied to any user starting a session on this server, or by def-
# ining profiles on a per-user basis. Any profile consists of a set
# of rules specifying what the user can or can't do in the session.
#
#EnableUserProfile = "0"

#
# Enable or disable clipboard:
#
# client: The content copied on the client can be pasted inside the
#         NX session.
#
# server: The content copied inside the NX session can be pasted
#         on the client.
#
# both:   The copy&paste operations are allowed between both the
#         client and the NX session and viceversa.
#
# none:   The copy&paste operations between the client and the NX
#         session are never allowed.
#
EnableClipboard = "both"

#
# Specify absolute path of the custom script to be executed before
# the user logs in. The script can accept remote IP of the user's
# machine as its input.
#
# E.g. UserScriptBeforeLogin = "/tmp/nxscript/script.sh"
#
#UserScriptBeforeLogin = ""

#
# Specify absolute path of the custom script to be executed after
# the user logs in. The script can accept username as its input.
#
#UserScriptAfterLogin = ""

#
# Specify absolute path of the custom script to be executed before
# the session start-up. The script can accept session ID, username
# node host and node port as its input.
#
#UserScriptBeforeSessionStart = ""

#
# Specify absolute path of the custom script to be executed after the
# session start-up. The script can accept session ID, username, node
# host and node port as its input.
#
#UserScriptAfterSessionStart = ""

#
# Specify absolute path of the custom script to be executed before
# the session is closed. The script can accept session ID, username,
# node host and node port as its input.
#
#UserScriptBeforeSessionClose = ""

#
# Specify absolute path of the custom script to be executed after the
# session is closed. The script can accept session ID, username, node
# host and node port as its input.
#
#UserScriptAfterSessionClose = ""

#
# Specify absolute path of the custom script to be executed before
# the session is reconnected. The script can accept session ID user-
# name, node host and node port as its input.
#
#UserScriptBeforeSessionReconnect = ""

#
# Specify absolute path of the custom script to be executed after the
# session is reconnected. The script can accept session ID username
# node host and node port as its input.
#
#UserScriptAfterSessionReconnect = ""

#
# Specify absolute path of the custom script to be executed before
# the session is suspended. The script can accept session ID, user-
# name, node host and node port as its input.
#
#UserScriptBeforeSessionSuspend = ""

#
# Specify absolute path of the custom script to be executed after
# the session is suspended. The script can accept session ID, user
# name, node host and node port as its input.
#
#UserScriptAfterSessionSuspend = ""

#
# Specify absolute path of the custom script to be executed before
# session failure. The script can accept session ID username, node
# host and node port as its input.
#
#UserScriptBeforeSessionFailure = ""

#
# Specify absolute path of the custom script to be executed after
# session failure. The script can accept session ID username, node
# host and node port as its input.
#
#UserScriptAfterSessionFailure = ""

#
# Specify absolute path of the custom script to be executed before
# NX Server creates the new account. The script can accept username
# as its input.
#
#UserScriptBeforeCreateUser = ""

#
# Specify absolute path of the custom script to be executed after
# NX Server has created the new account. The script can accept user-
# name as its input.
#
#UserScriptAfterCreateUser = ""

#
# Specify absolute path of the custom script to be executed before
# NX Server removes the account. The script can accept username as
# its input.
#
#UserScriptBeforeDeleteUser = ""

#
# Specify absolute path of the custom script to be executed after
# NX Server has removed the account. The script can accept username
# as its input.
#
#UserScriptAfterDeleteUser = ""

#
# Specify absolute path of the custom script to be executed before
# NX Server disables the user. The script can accept username as its
# input.
#
#UserScriptBeforeDisableUser = ""

#
# Specify absolute path of the custom script to be executed after
# NX Server has disabled the user. The script can accept username
# as its input.
#
#UserScriptAfterDisableUser = ""

#
# Specify absolute path of the custom script to be executed before
# NX Server enables the user. The script can accept username as its
# input.
#
#UserScriptBeforeEnableUser = ""

#
# Specify absolute path of the custom script to be executed after
# NX Server has enabled the user. The script can accept username
# as its input.
#
#UserScriptAfterEnableUser = ""

#
# Allow session shadowing on this server:
#
# 1: Enabled. User can require to attach to an already running
#    session. The session owner has to accept connection.
#
# 0: Disabled. Session shadowing is forbidden.
#
#EnableSessionShadowing = "1"

#
# Allow session shadowing in interactive mode:
#
# 1: Enabled. User attaching to the session can interact with
#    the session.
#
# 0: Disabled. The session is shadowed in view-only mode. User 
#    attaching to the session can't interact with the session.
#
#EnableInteractiveSessionShadowing = "1"

#
# Enable or disable NX server requiring authorization to the owner
# of the NX session before sharing the session.
#
# 1: Enabled. NX server asks for authorization to the owner
#    of the master session before trying to share the session.
#
# 0: Disabled. NX server tries to share the NX session without
#    the need of any authorization from the owner of the master
#    desktop.
#
#EnableSessionShadowingAuthorization = "1"

#
# Allow desktop sharing on this server:
#
# 1: Enabled. User can require to attach to the native display
#    of the nodes. The desktop's owner has to accept connection.
#
# 0: Disabled. Desktop sharing is forbidden.
#
#EnableDesktopSharing = "1"

#
# Allow the NX user to connect to a desktop owned by a user who is
# not an NX user:
#
# 1: Enabled. Allow an NX user to connect to a desktop owned
#    by a user who is not an NX user. This requires running a
#    privileged script as root and will work only if the node.
#    is the same machine where NX server is running.
#
# 0: Disabled. An NX user can connect only to a desktop owned
#    by an NX user when EnableDesktopSharing is enabled.
#
#EnableFullDesktopSharing = "0"

#
# Allow desktop sharing in interactive mode:
#
# 1: Enabled. User attaching to the desktop can interact with
#    the session.
#
# 0: Disabled. The session is shadowed in view-only mode. User
#    attaching to the desktop can't interact with the session.
#
#EnableInteractiveDesktopSharing = "0"

#
# Enable or disable NX server requiring authorization to the owner
# of the desktop before sharing the session.
#
# 1: Enabled. NX server asks for authorization to the owner
#    of the desktop.
#
# 0: Disabled. NX server tries to share the native display
#    without the need of any authorization from the owner
#    of the desktop.
#
#EnableDesktopSharingAuthorization = "1"

#
# Enable or disable NX server requiring authorization before sharing
# the session either when the X server is running as root or gdm.
#
# 1: Enabled. NX server needs authorization to proceed with
#    sharing the session.
#
# 0: Disabled. NX server tries to share the native display
#    without the need for any authorization. Sharing the
#    session is also possible when a user is not logged
#    on to the local desktop.
# 
#EnableSystemDesktopSharingAuthorization = "1"

#
# Allow the server to set disk quota for the guest accounts:
#
# 1: Enabled. When a new guest account is created on the system,
#    the server will set the disk quota for this user.
#
# 0: Disabled. No restrictions on the amount of disk space used
#    by each guest user are applied.
#
#EnableGuestQuota = "0"

#
# Specify the username of the account to be used as a protoype for
# propagating its disk quota settings to all the new guest accounts.
# If the softlimit or the hardlimit on either the inode or the disk
# block are set, they will override the settings applied to the user
# prototype.
#
#GuestQuotaProtoname = "protoguest"

#
# Specify the maximum amount of disk space available for each of the
# guest users, checked as number of inodes. This limit can be exceeded
# for the grace period.
#
#GuestQuotaInodeSoftlimit = "0"

#
# Specify the absolute maximum amount of disk space available for
# each of the guest users, checked as number of inodes. Once this
# limit is reached, no further disk space can be used.
#
#GuestQuotaInodeHardlimit = "0"

#
# Specify the maximum amount of disk space available for each of the
# guest users, checked as number of disk blocks consumed. This limit
# can be exceeded for the grace period.
#
#GuestQuotaBlockSoftlimit = "0"

#
# Specify the absolute maximum amount of disk space available for each
# of the guest users, checked as number of disk blocks consumed. Once
# this limit is reached, no further disk space can be used.
#
#GuestQuotaBlockHardlimit = "0"

#
# Specify the grace period, expressed in seconds, during which the
# soft limit, set in the GuestQuotaInodeSoftlimit key may be
# exceeded.
#
#GuestQuotaInodeGracePeriod = "0"

#
# Specify the grace period, expressed in seconds, during which the
# soft limit, set in the GuestQuotaBlockSoftlimit key may be
# exceeded.
#
#GuestQuotaBlockGracePeriod = "0"

#
# Specify a list of comma-separated filesystem names or devices to
# which the disk quota restrictions will be applied. The default
# value is 'all' which corresponds to applying the disk quota limits
# to all the filesystems having disk quota enabled.
#
#GuestQuotaFilesystems = "all"

#
# Sets path and name of the command 'sessreg'.
#
#CommandSessreg = "/usr/X11R6/bin/sessreg"

```

sshd
```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 2022
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 4096

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
MaxAuthTries 5

RSAAuthentication no
PubkeyAuthentication yes
AuthorizedKeysFile %h/.ssh/authorized_keys
#AuthorizedKeysFile %h/.ssh/authorized_keys2
AuthorizedKeysFile2 /usr/NX/home/nx/.ssh/authorized_keys2
#AuthorizedKeysFile2 /var/lib/nxserver/home/.ssh/authorized_keys2
#AuthorizedKeysFile /var/lib/nxserver/home/.ssh/authorized_keys


# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes
IgnoreUserKnownHosts yes
PasswordAuthentication no
GatewayPorts no
AllowTcpForwarding yes
KeepAlive yes
ChallengeResponseAuthentication no
RhostsRSAAuthentication no
HostbasedAuthentication no
AllowUsers nx FRED

```

---

### Post by MrDetermination on 2011-01-08
bump

---

### Post by MrDetermination on 2011-01-09
bump

---

### Post by MrDetermination on 2011-01-10
bump

---

