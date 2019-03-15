# Tratamento de Erros

Um [Erro](#error) possui alguns campos que permitem identificar a causa do problema.

## code

Através do `code` é possível identificar o grupo ao qual o Erro pertence. A maioria deles possui um campo `sub_errors` com detalhes mais específicos. São estes os grupos:

- `internal_server_error`: Erro interno da aplicação.

- `bad_request`: Requisição mal construída. Normalmente acontece quando o body não corresponde ao formato esperado.

- `not_found`: Recurso não encontrado.

- `unauthorized`: Não autorizado. Representa algum problema de autenticação com a API.

- `validation_error`: Erro de validação. Significa que algum valor passado é inválido. Neste caso, cada Sub-Erro possui `field` com o nome do campo inválido.

- `transfer_error`: Transferência falhou.

- `insecure_connection`: Conexão insegura. (É obrigatório que todas as chamadas utilizem `https`)

## msg

É uma mensagem legível sobre a causa do problema.

## sub_errors

[`sub_errors`](#suberror) contém uma lista de Sub-Erros com detalhes específicos sobre a causa do problema.
Assim como o Error, ele possui `code`, `msg` (e `field` em caso de Erro de validação):

### `not_found`

- `org_not_found`: Organização não encontrada.



### `validation_error`

- `pagination_limit`: O campo 'limit' de Paginação deve ser um número positivo 

- `pagination_starting_after`: O campo 'starting_after' de Paginação deve ser um número positivo 

- `invalid_token`: Token inválido 

- `org_name_already_exists`: Já existe uma Organização com este nome 

- `org_name_empty`: O nome da Organização não pode ser vazio 

- `org_network_required`: O campo 'Network' é obrigatório 

- `ast_code_is_empty`: Código do Ativo não pode ser vazio

- `ast_code_invalid`: Código do Ativo inválido; apenas letras e números são permitidos

- `ast_code_already_exists`: Já existe um Ativo com este código

- `ast_code_invalid_length`: Quantidade de caracteres inválida para código do Ativo; máximo de 12 caracteres

- `ast_invalid_limit`: Limite do Ativo inválido

- `ast_not_supported`: Ativo não suportado 

- `transfer_from_is_empty`: Remetente da Transferência não pode ser vazio.

- `transfer_to_is_empty`: Destinatário da Transferência não pode ser vazio.

- `transfer_asset_id_is_empty`: Asset não pode ser vazio na Transferência.

- `transfer_invalid_amount`: A quantidade a ser transferida é inválida.

- `transfer_invalid_actions_length`: Número inválido de Transferências no lote.

- `act_invalid_actions_length`: Quantidade de Ações inválida no lote.

- `tag_invalid_value`: Valor inválido. Tags devem ser compostas somente de caracteres alfanuméricos e/ou `-_\/|:`, e ter tamanho entre 2 e 200.

- `tag_invalid_size`: Limite de tags excedido. O número máximo é de 10 tags por entidade.

### `transfer_error`

- `transfer_asset_not_found`: Ativo não encontrado.

- `transfer_from_not_found`: Remetente não encontrado.

- `transfer_to_not_found`: Destinatário não encontrado.

- `transfer_to_asset_not_supported`: Ativo não suportado pela Conta destinatária.

- `transfer_from_asset_not_supported`: Ativo não suportado pela Conta remetente.

- `transfer_underfunded`: Saldo insuficiente para a Transferência.

### `unauthorized`

- `acc_should_not_have_balances`: Conta não pode ser destruída a não ser que todos os seus saldos sejam zero