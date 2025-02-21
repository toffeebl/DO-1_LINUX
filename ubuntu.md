# UNIX/Linux operating systems (Basic).

## Part 1. Installation of the OS
##### 1.Ubuntu 20.04 Server LTS without GUI is installed.

##### 2.`cat /etc/issue` command is run

![Alt text](<screen report/installation of ubuntu 20.04.png>)

## Part 2. Creating a user

##### 1.Created a new user.

* `sudo useradd -g adm jackie`
![Alt text](<screen report/new user added-1.png>)

##### 2.`cat /etc/passwd`
![Alt text](<screen report/command cat.png>)

## Part 3. Setting up the OS network
##### 1.Set the machine name as user-1

* `sudo hostnamectl set-hostname user-1`
![Alt text](<screen report/set hostname.png>)

* `hostname`
![Alt text](<screen report/hostname changed-1.png>)

##### 2.set the time zone corresponding to a current location

![Alt text](<screen report/time zone.png>)

##### 3. Output the names of the network interfaces

![Alt text](<screen report/names of network interfaces.png>)

**== explanation of lo interface ==**

* The "lo" interface is a special network interface in Linux that represents the loopback interface. It is often referred to as "localhost" or "loopback" interface. It is commonly used for testing network applications and services locally on a machine.This interface is identified by the IP address 127.0.01, which is known as the loopback address.

##### 4.Use the console command to get the ip address of the device you are working on from the DHCP server.

![Alt text](<screen report/ip address.png>)

**== explanation of DHCP ==**

* DHCP stands for Dynamic Host Configuration Protocol. It's a network management protocol used on IP networks where a DHCP server automatically assigns and manages IP addresses and other network configuration parameters to devices connected to the network.DHCP simplifies the process of network configuration by dynamically allocating IP addresses to devices as they connect to the network, rather than requiring manual configuration of each device's network settings. 

##### Display the external ip address of the gateway (ip) and the internal IP address of the gateway, aka default ip address (gw).

![Alt text](<screen report/ip route.png>)

![Alt text](<screen report/gateway ip.png>)

**== internal ip ==**

![Alt text](<screen report/internal ip.png>)

##### Set static (manually set, not received from DHCP server) ip, gw, dns settings (use public DNS servers, e.g. 1.1.1.1 or 8.8.8.8).

![Alt text](<screen report/config file 1.png>)

![Alt text](<screen report/static ip.png>)

![Alt text](<screen report/apply netplan changes.png>)

##### Reboot the virtual machine. Make sure that the static network settings (ip, gw, dns) correspond to those set in the previous point.

![Alt text](<screen report/reboot.png>)

##### ping 1.1.1.1 and ya.ru remote hosts

![Alt text](<screen report/ping 1.1.1.1.png>)

![Alt text](<screen report/ping ya.ru.png>)

## Part 4. OS Update

##### Update the system packages to the latest version

![Alt text](<screen report/update the system packages.png>)

## Part 5. Using the **sudo** command

##### Sudo is used to access restricted files and operations. By default, Linux restricts access to certain parts of the system preventing sensitive files from being compromised.The sudo command temporarily elevates privileges allowing users to complete sensitive tasks without logging in as the root user.

##### Allow user created in [Part 2](#part-2-creating-a-user) to execute sudo command.

![Alt text](<screen report/change hostname.png>)

## Part 6. Installing and configuring the time service

##### Set up the automatic time synchronisation service.
##### - The output of the following command must contain `NTPSynchronized=yes`: \
  
  * `timedatectl show`

![Alt text](<screen report/syncronized time.png>)

## Part 7. Installing and using text editors

##### 1.Install **VIM** text editor (+ any two others if you like **NANO**, **MCEDIT**, **JOE** etc.)

##### 2.Using each of the three selected editors, create a *test_X.txt* file, where X is the name of the editor in which the file is created. Write your nickname in it, close the file and save the changes.

* `sudo apt-get install vim`
* `sudo apt-get install mcedit`
* `sudo apt-get install nano`

##### 3.Using each of the three selected editors, open the file for editing, edit the file by replacing the nickname with the "21 School 21" string, close the file without saving the changes. 

##### 4.Using each of the three selected editors, edit the file again (similar to the previous point) and then master the functions of searching through the contents of a file (a word) and replacing a word with any other one.

## VIM
1.![Alt text](<screen report/vim installation.png>)

2![Alt text](<screen report/Vim nickname.png>)

3.![Alt text](<screen report/vim 21s.png>)
 
4.![Alt text](<screen report/vim search.png>)
 
5.![Alt text](<screen report/vim replace.png>)

6.![Alt text](<screen report/vim replaced.png>)

* `vim test_VIM.txt`

* Switch to Insert mode:I

* Save the file and quit: :wq

* Quit without saving: :q

* / < text that we want to search>

* :s/<search_phrase>/<replace_phrase>

## NANO
1.![!Alt text](<screen report/nano nickname-1.png>)

2.![Alt text](<screen report/nano 21s.png>)

3.![Alt text](<screen report/nano search.png>)

4.![Alt text](<screen report/nano replace 1.png>)

5.![Alt text](<screen report/nano replace 2.png>)

6.![Alt text](<screen report/nano replaced.png>)

* `nano test_NANO.txt`

* Save the file and quit:CTRL+x, y+enter

* Quit without saving:CTRL+x, n+enter

* Search: Ctrl + W

* A search and replace:Alt+R

## MCEDIT
1.![Alt text](<screen report/mcedit nickname.png>)

2.![Alt text](<screen report/mcedit 21s.png>)

3.![Alt text](<screen report/mcedit search.png>)

4.![Alt text](<screen report/mcedit search 2.png>)

5.![Alt text](<screen report/mcedit replace.png>)

6.![Alt text](<screen report/mcedit replace2.png>)

7.![Alt text](<screen report/mcedit replaced.png>)

* `mcedit test_MCEDIT.txt`

* Save the file and quit:F2(yes)+F10

* Quit without saving:F10(no)

* Search:F7+< text we want to search>

* A search and replace:F4+< search phrase>+<replace_phrase>

## Part 8. Installing and basic setup of the **SSHD** service

##### 1.Install the SSHd service.

* `sudo apt install openssh-server`

![Alt text](<screen report/install ssh.png>)

##### 2.Add an auto-start of the service whenever the system boots.

* `sudo systemctl enable ssh`

* `systemctl status ssh`

![Alt text](<screen report/autostart ssh.png>)

##### 3.Reset the SSHd service to port 2022.

* `sudo vim /etc/ssh/sshd_config`

![Alt text](<screen report/ssh port 2022.png>)

* `systemctl restart sshd`

##### 4.Show the presence of the sshd process using the ps command. To do this, you need to match the keys to the command.

![Alt text](<screen report/ps command.png>)

The ‘ps’ command ‘process status’, its primary function is to report a snapshot of the current processes in a system.

* ps -e Displays information about all processes.
* ps -f	Provides full-format listing.	
* ps -l	Displays long format listing.  
* ps -j	Displays jobs format.	
* ps -o	User-defined format.
* ps -p	Select by PID.
* ps -t	Select by TTY.
* ps -u	Select by effective user ID (EUID).
* ps -x	List processes without controlling terminals.
* ps -C	Select by command name.
* ps -L	Show threads, possibly with LWP and NLWP columns.

##### Reboot the system.
 
## NETSTAT
* `netstat -tan`

![Alt text](<screen report/ssh port changed-1.png>)

* -t (--tcp) displays connections via tcp only
* -a (--all) output all active TCP connections
* -n (--numeric) display active TCP connections, displaying addresses and port numbers in numeric format
* Proto: Protocol name (TCP protocol or UDP protocol);
* recv-Q: network receive queue
* send-Q: Network send queue
* Local Address: address of the local computer and port number used
* Foreign Address: address and number of the remote computer to which the socket is connected
* State socket state
* 0.0.0.0 means IP address on local machine

## Part 9. Installing and using the **top**, **htop** utilities

- From the output of the top command determine and write in the report:
    - uptime: 1:34
    - number of authorised users: 1
    - total system load:0.00, 0.00, 0.00
    - total number of processes:96
    - cpu load:0.0
    - memory load:3920.2
    - pid of the process with the highest memory usage:676
    - pid of the process taking the most CPU time: 361

- Add a screenshot of the htop command output to the report:
    - sorted by PID, PERCENT_CPU, PERCENT_MEM, TIME
    ## PID
   ![Alt text](<screen report/PID.png>)

    ## PERCENT_CPU
    ![Alt text](<screen report/PERCENT_CPU.png>)

    ##  PERCENT_MEM
   ![Alt text](<screen report/PERCENT_MEM.png>)

    ## TIME
    ![Alt text](<screen report/TIME.png>)
   
    - filtered for sshd process
    ![Alt text](<screen report/sshd process htop.png>)

    - with the syslog process found by searching
    ![Alt text](<screen report/htop syslog-1.png>)

    - with hostname, clock and uptime output added
    ![Alt text](<screen report/host clock time.png>)

## Part 10. Using the **fdisk** utility

##### Run the fdisk -l command.
![Alt text](<screen report/fdisk.png>)
* the name of the hard disk-VBOX HARDDISK
* capacity-20.51GiB
* number of sectors-42988544
* the swap size 
![Alt text](<screen report/swap size.png>)

## Part 11. Using the **df** utility
##### Run the df command.
- In the report write for the root partition (/):
    - partition size-10218772
    - space used-3164184
    - space free-6513916
    - percentage used-33
- Determine and write the measurement unit in the report.-kilobayt

##### Run the df -Th command.
- In the report write for the root partition (/):
    - partition size-9.8G
    - space used-3.1G
    - space free-6.3G
    - percentage used-33%
- Determine and write the file system type for the partition in the report-ext4

![Alt text](<screen report/df command.png>)

## Part 12. Using the **du** utility

##### Run the du command.
##### Output the size of the /home, /var, /var/log folders (in bytes, in human readable format)

![Alt text](<screen report/du command-1.png>)

##### Output the size of all contents in /var/log (not the total, but each nested element using *)

![Alt text](<screen report/var log.png>)

## Part 13. Installing and using the **ncdu** utility

##### Install the ncdu utility.
* sudo apt install ncdu
![Alt text](<screen report/installation of ncdu.png>)
##### Output the size of the /home, /var, /var/log folders.

## /home
![Alt text](<screen report/ncdu_home.png>)
 
 ## /var
 ![Alt text](<screen report/ncdu_var.png>)
 
 ## /var/log
![Alt text](<screen report/ncdu_var_log.png>)
 ## Part 14. Working with system logs

* 1.`sudo vim /var/log/dmesg`
* 2.`sudo vim /var/log/syslog`
* 3.`sudo vim /var/log/auth.log`

- Write the last successful login time, user name and login method-11:52:51 toffeebl by LOGIN
- Restart SSHd service

- Add a screenshot of the service restart message to the report (search for it in the logs).

![Alt text](<screen report/restar ssh server.png>)

## Part 15. Using the **CRON** job scheduler

##### Using the job scheduler, run the uptime command in every 2 minutes.- Find lines in the system logs (at least two within a given time range) about the execution;
- Display a list of current jobs for CRON;
- Add screenshots of the execution lines and the list of current tasks to the report.

![Alt text](<screen report/cron.png>)

![Alt text](<screen report/report cron.png>)
##### Remove all tasks from the job scheduler.
- Add a screenshot of the list of current tasks for CRON to the report.
![Alt text](<screen report/cron empty.png>)