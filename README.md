# formulario-php
Código criar formulário

<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulário</title>
<style>
    /*estilo geral da pagina*/
    body{
        font-family: Arial, Helvetica, sans-serif;
        background: linear-gradient(to right, rgb(10, 9, 9), rgb(116, 22, 22));
        color: white;
    }

    .modelo{
        width: 340px;
        height: 685px;
        margin: 100px auto;
        background-color: rgb(19, 18, 18);
        border: 10px double rgb(134, 51, 51);
        border-radius: 15px;
        padding: 20px;
    }
    </style>
</head>
<body>
    <div class="modelo">
        <form method="POST" action="">
            <h2 align="center">Formulário de clientes</h2>
            Nome: <br>
            <input type="text" name="nome" size="40" required>
            <br><br>
            Email: <br>
            <input type="text" name="email" size="40" required>
            <br><br>
            Telefone: <br>
            <input type="text" name="telefone" size="40" required>
            <br><br>
            Sexo: <br>
            <input type="radio" name="genero" value="Masculino" required>Masculino
            <input type="radio" name="genero" value="Feminino" required>Feminino
            <input type="radio" name="genero" value="Outro" required>Outro
            <br><br>
            Data de nascimento: <br>
            <input type="date" name="nasc" required>
            <br><br>
            Endereço: <br>
            <input type="text" name="endereco" size="40" required>
            <br><br>
            Cidade: <br>
            <input type="text" name="cidade" size="40" required>
            <br><br>
            Estado: <br>
            <input type="text" name="estado" size="40" required>
            <br><br>
            Escreva uma Mensagem: <br>
            <textarea name="mensagem" rows="4" cols="40" required></textarea>
            <br><br><br>
            <center><input type="submit" value="Enviar" name="acao"></center>
            <br><br> 

        </form>

        <?php

        if(isset ($_POST["acao"])) {
        $nome = $_POST['nome'];
        $email = $_POST['email'];
        $telefone = $_POST['telefone'];      
        $sexo = $_POST['genero'];
        $nasc = $_POST['nasc'];
        $endereco = $_POST['endereco'];
        $cidade = $_POST['cidade'];
        $estado = $_POST['estado'];
        $mensagem = $_POST['mensagem'];

        require "config.php";

        $result = mysqli_query($conexao, "INSERT INTO cliente (nome, email, telefone, sexo, nascimento, endereco, cidade, estado, mensagem)
        VALUES ('$nome', '$email', '$telefone', '$sexo', '$nasc', '$endereco', '$cidade', '$estado', '$mensagem')");

        header ("Location: formulario.php");

        exit;
        }
        ?>
    </div>
</body>
</html>
