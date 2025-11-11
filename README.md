# 🚀 Solução de configuração: make no PowerShell para `make deploy`

Este guia detalha os passos realizados para instalar o `make` no ambiente Windows/PowerShell (via Winget) e corrigir o erro de ambiente para que o comando `make` seja reconhecido.

## 1. Instalação da ferramenta `make` no Windows

O `make` não é nativo do Windows. Utilizamos o gerenciador de pacotes Winget para instalar uma versão compatível (GnuWin32).

### 1.1. Comando de instalação (PowerShell)

Execute este comando no seu terminal PowerShell para instalar o `make`:

```powershell
winget install GnuWin32.Make
```

## 2. Correção de Erro de Ambiente (Variável PATH)

Após a instalação, se você receber o erro:

```
make : O termo 'make' não é reconhecido...
```

significa que o local do executável `make.exe` não está na variável de ambiente `PATH` do Windows.

### 2.1. Local do executável

O `make` foi instalado no seguinte diretório (por padrão):

```
C:\Program Files (x86)\GnuWin32\bin
```

### 2.2. Ação de correção (Adicionar ao PATH)

Para adicionar esse diretório às Variáveis de Ambiente do Sistema do Windows:

1. Abra o menu Iniciar e pesquise por "variáveis de ambiente".
2. Clique em "Editar as variáveis de ambiente do sistema".
3. Na janela "Propriedades do Sistema", clique em "Variáveis de Ambiente...".
4. Na seção "Variáveis do sistema", selecione a variável `Path` e clique em "Editar...".
5. Clique em "Novo" e insira o caminho:
   ```
   C:\Program Files (x86)\GnuWin32\bin
   ```
6. Clique em "OK" em todas as janelas para salvar as alterações.

Importante: abra (ou reinicie) o VS Code e o PowerShell para que o novo `PATH` seja carregado na sessão.

## ✅ Execução Final

Com o `make` instalado e o `PATH` configurado, execute o comando a partir do diretório do seu projeto (ex.: `C:\n8n`):

```powershell
make deploy
```

Pronto — agora o `make` deve ser reconhecido no PowerShell e o comando `make deploy` deve funcionar conforme esperado.
