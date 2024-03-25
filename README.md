# Grupo 04N:
  Patrick Alves Gonçalves - 42214440 - 10409363
  
  Nicholas dos Santos Leal - 42210771 - 10409210
  
  Gustavo Ibara - 42210720 – 10389067
  

# 1) Considere o exemplo fornecido para troca de mensagens entre pai e filho. Altere o programa de modo que a alteração da variável value se reflita no processo pai, ou seja, o último print do programa deve apresentar o seguinte resultado: PARENT: value = 20

  Para realizarmos esse exercício, pegamos o código enviado e fizemos as seguintes alterações no código:
  
  Antes de chamar a função fork(), criamos um pipe usando a função pipe(fd). Isso retorna dois descritores de arquivo: fd[0] para leitura e fd[1] para escrita.
  
  No processo filho (quando pid == 0), após incrementar a variável value, escrevemos o valor modificado no pipe usando a função: write(fd[1], &value, sizeof(value)).
  
  No processo pai (quando pid > 0), após esperar o processo filho terminar com a função: wait(NULL), lemos o valor do pipe usando a função read(fd[0], &value, sizeof(value)). 
  
  Isso nos dá o valor que foi escrito pelo processo filho.
