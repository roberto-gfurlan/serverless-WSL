# # ALTU Serverless rodando no Windows com WSL

Olá, esse tutorial foi feito para auxiliar a configuração correta do WSL e a integração com o docker. 🚀

*Escrito por Roberto Furlan com colaboração de Flavio Kicis*

---

## WSL

Verifique qual a versão do WSL e se o Ubuntu já está instalado. Abra
    o Comand Prompt digite o seguinte:
    
```
    wsl --list  --verbose
```
Se sua resposta for igual a essa:

![enter image description here](https://i.imgur.com/unLkFeM.png)

 Parabéns, vá para a etapa [Rodando o ALTU Serverless no WSL](#rodando-o-altu-seerveles-no-wsl). Se não, siga o próximo passo. 👇

1. Para ajustar a sua versão do WSL, baixe o pacote de atualização do kernel [aqui] (https://docs.microsoft.com/pt-br/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package) e rode, depois abra o Power Shell e rode o seguinte comando:
 ```
  wsl --set-default-version 2 
  ```

3. Caso o **Ubuntu** ainda não esteja instalado, vá até a **Microsoft Store** e baixe a versão desejada
![enter image description here](https://i.imgur.com/Jn1PbZ9.png)

5. Após a instalação, clicar no App do Ubuntu no **Menu Iniciar** para finalizar a instalação.

6. Instale também o **Windows Terminar** pela **Mircrosoft Store** para facilitar o uso de diferentes Shells.

7. No Windows Terminal, abra uma shell do Ubuntu e teste se o WSL está conectado na internet com o seguinte código
 ```
ping google.com
 ```
 
8. Se der falha de conexão, vá para home com `cd ~`  e rode:

 ``` 
sudo rm /etc/resolv.conf
sudo bash -c 'echo "nameserver 8.8.8.8" > /etc/resolv.conf'
sudo bash -c 'echo "[network]" > /etc/wsl.conf'
sudo bash -c 'echo "generateResolvConf = false" >> /etc/wsl.conf'
sudo chattr +i /etc/resolv.conf
 ```


 9. Com a conexão, rode `sudo apt-get update`
 10. Verifique a sua versão do NodeJs `node --version` , se for inferior a versão 12, faça o upgrade. Primeiro instale o npm, `npm install npm@latest -g`, depois `sudo npm cache clean -f`, `sudo npm install -g n` e `sudo n stable`
***

## Rodando o Altu Serveles no WSL

1. Verifique se o seu Docker Desktop está conectado com o Ubuntu em: `Configurações > Resources > WSL Integration`
2. Abra o **Windows Terminal** em uma shell do **Ubuntu**.
3. Navegue até a pasta clonada do repositório.
4. Dentro da pasta digite `code .` para abrir o WSL no VSCODE. Agora você está rodando a pasta dentro do sistema Linux.
5. No Vscode, rode `npm install`, depois `sudo make up` para iniciar os containers.
6. Em outra aba do terminal digite `make sh` para entrar no container.
7. No container rode `npm start offline:xxxxx`
8. Pronto o serveles já está rodando localmente!
