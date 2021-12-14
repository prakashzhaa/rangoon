# Rangoon

```                ___
      ///////      / \	   ||\	    ||   |||||||     ||||||    ||||||	||\ 	 ||
    ||      ||    // \\    || \	    ||  ||	    ||    ||  ||    ||	|| \ 	 ||
    ||	    ||	 //   \\   ||  \    ||  ||	    || 	  ||  ||    ||	||  \ 	 ||
    ||///////   //     \\  ||   \   ||  ||   ||||   ||    ||  ||    ||	||   \ 	 ||
    ||\/\      ||||||||||| ||	 \  ||  ||  ||  ||  ||    ||  ||    ||	||    \	 ||
    || \/\     ||	|| ||	  \ ||  ||  ||  ||  ||    ||  ||    ||	||     \ ||
    ||  \/\    ||	|| ||	   \||  ||  ||  ||  ||    ||  ||    ||	||      \||
    ||   \/\   ||	|| ||	    ||   ||||	||   ||||||    ||||||	||       ||                                                 
                                                                      @prakashzhaa 

```


*Rangoon** automates the entire process of reconnaisance for you. It outperforms the work of subdomain enumeration along with various vulnerability checks and obtaining maximum information about your target.

rangoon uses lot of techniques (passive, bruteforce, certificate transparency, source code scraping, analytics, DNS records...) for subdomain enumeration which helps you getting the maximum and the most interesting subdomains so that you be ahead of the competition.

It also performs various vulnerability checks like XSS, Open Redirects, SSRF, CRLF, LFI, SQLi, SSL tests, SSTI, DNS zone transfers, and much more. Along with these, it performs OSINT techniques, directory fuzzing, dorking, ports scanning, screenshots, nuclei scan on your target.


### Easy installation

Now we can set up everything, it's quite simple:

 - `git clone https://github.com/prakashzhaa/rangoon.git`
 - `cd rangoon`
 - `chmod +x install.sh`
 - `chmod +x rangoon.sh`
 - `./install.sh`

Grab a cup of coffee since this will take a while.

## Usage

After installing all of the dependencies for the rangoon you can finally start doing some recon!

```
$ rangoon <domain.tld>
```

`rangoon.sh` will first gather resolvers for the given target, followed by subdomain enumeration and checking those assets for potential subdomain takeover. When this is done the IP addresses of the target are enumerated. Open ports will be discovered accompanied by a service scan provided by Nmap.

Nuclei and its templates have been implemented in the routine!

Finally the live targets will be screenshotted and evaluated to discover endpoints.

Results will be stored on the rangoon and can be viewed by running `python -m SimpleHTTPServer 1337" in your results directory. Your results will be accessible from any system with a browser that exists in the same network. 

Make sure to add your SLACK token to the tokens.txt file if you want to get slack notification after the completion of recon process.

## Sample Token.txt ($HOME/rangoon/configs/tokens.txt)

```
github_subdomains_token=""
SLACK_WEBHOOK_URL="https://hooks.slack.com/services/xxx/xxx/xxx"
findomain_spyse_token=""
findomain_virustotal_token=""
findomain_securitytrails_token=""
CHAOS_KEY=""
hackerhandle="rangoon"
```

## Config Files (Note: config file for amass, subfinder and naabu are stored inside rangoon/configs/ folder, provide your api keys in these files)

**Input your API keys in these files to get better results**

Subfinder Config file path : $HOME/rangoon/configs/config.yaml

Amass Config file path : $HOME/rangoon/configs/config.ini

We have added a `$hackerhandle` which is used in the nuclei scans. An additional `x-bug-bounty: rangoon` header will be added, please update this with your own handle :) 

## Scripts

- Script folder contains a script named **daily** which can be used as a cronjob to run subdomain enumeration automatically.

- Methodology is to take already enumerated subdomains as input and use amass on top of them, then track their last 2 result, and alert new subdomains on slack.

## Tools

Tools that will be installed:
- [Go](https://github.com/golang)
- [Subfinder](https://github.com/projectdiscovery/subfinder/cmd/subfinder)
- [Subjack](https://github.com/haccer/subjack)
- [Aquatone](https://github.com/michenriksen/aquatone)
- [httprobe](https://github.com/tomnomnom/httprobe)
- [assetfinder](https://github.com/tomnomnom/assetfinder)
- [meg](https://github.com/tomnomnom/meg)
- [tojson](https://github.com/tomnomnom/hacks/tojson)
- [unfurl](https://github.com/tomnomnom/unfurl)
- [gf](https://github.com/tomnomnom/gf)
- [anew](https://github.com/tomnomnom/anew)
- [qsreplace](https://github.com/tomnomnom/qsreplace)
- [ffuf](https://github.com/ffuf/ffuf)
- [gobuster](https://github.com/OJ/gobuster)
- [amass](https://github.com/OWASP/Amass)
- [getJS](https://github.com/003random/getJS)
- [gau](https://github.com/lc/gau)
- [shuffledns](https://github.com/projectdiscovery/shuffledns/cmd/shuffledns)
- [dnsprobe](https://github.com/projectdiscovery/dnsprobe)
- [naabu](https://github.com/projectdiscovery/naabu/cmd/naabu)
- [nuclei](https://github.com/projectdiscovery/nuclei/cmd/nuclei)
- [nuclei-template](https://github.com/projectdiscovery/nuclei-templates)
- [cf-check](https://github.com/dwisiswant0/cf-check)
- [massdns](https://github.com/blechschmidt/massdns)
- [jq](https://stedolan.github.io/jq/)
- [masscan](https://github.com/robertdavidgraham/masscan)
- [Corsy](https://github.com/s0md3v/Corsy)
- [Arjun](https://github.com/s0md3v/Arjun)
- [Diggy](https://github.com/s0md3v/Diggy)
- [Dnsgen](https://github.com/ProjectAnte/dnsgen)
- [Sublert](https://github.com/yassineaboukir/sublert)
- [Findomain](https://github.com/Edu4rdSHL/findomain)
- [github-subdomain](https://raw.githubusercontent.com/gwen001/github-search/master/github-subdomains.py)
- [linkfinder](https://github.com/GerbenJavado/LinkFinder)
- [bass](https://github.com/Abss0x7tbh/bass)
- [interlace](https://github.com/codingo/Interlace)
- [nmap](https://nmap.org)
- [Seclist](https://github.com/danielmiessler/SecList)
- [Dirsearch](https://github.com/maurosoria/dirsearch)
- [Dalfox](https://github.com/hahwul/dalfox)
- [Hakrawler](https://github.com/hakluke/hakrawler)
- [Naabu](https://github.com/projectdiscovery/naabu)
- [chaos](https://github.com/projectdiscovery/chaos-client)
- [httpx](https://github.com/projectdiscovery/httpx)
- [altdns](https://github.com/infosec-au/altdns)

## Methodology
- gatherResolvers
- gatherSubdomains
- checkTakeovers
- getCNAME
- gatherIPs
- gatherScreenshots
- startMeg
- fetchArchive
- fetchEndpoints
- runNuclei
- portScan
- notifySlack

**Subdomain Enumeration:**
- Sublert
- Subfinder
- assetfinder
- amass
- findomain (Add findomain sources token to get better result)
- chaos dataset
- github-subdomains
- dns.bufferover.run
- Mutate above Subdomains using commonspeak subdomain list

- Combine and Sort above result -> Use shuffledns to resolve -> dnsgen(to mutate) -> httprobe (to get alive hosts)

- Check takeover using subjack and nuclei

- Get CNAME to check manually for takeovers

- Use dnsprobe to gather IP, ignore if they fall in cloudflare ip range

- Do masscan and then nmap scan on them, also use http-title and vulners script.

- Take Screenshot for visual recon

- Use gau to to get archive urls, get paramlist, jsurls, phpurls, aspxurls, and jspurls in there own files.

- Get Endpoints using Linkfinder

- Run Nuclei Scripts on alive hosts

- Notify on Slack channel if token is specified.

- Directory Buteforcing (Not enabled, as it takes long time, it is better to do manually)

More tools will be added in the future, feel free to make a pull request!
**#Disclaimer**
Usage of this program for attacking targets without consent is illegal. It is the user's responsibility to obey all applicable laws. The developer assumes no liability and is not responsible for any misuse or damage caused by this program. Please use responsibly.

The material contained in this repository is licensed under GNU GPLv3.
